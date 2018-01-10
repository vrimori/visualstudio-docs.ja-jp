---
title: "ビルドのカスタマイズ | Microsoft Docs"
ms.custom: 
ms.date: 06/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
caps.latest.revision: "13"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 78773b3a87aff91fae92ec64365ef55620e58d44
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="customize-your-build"></a>ビルドのカスタマイズ
バージョン 15 より前のバージョンの MSBuild では、ソリューション内のプロジェクトに新しいカスタム プロパティを提供する場合、ソリューション内のすべてのプロジェクト ファイルにそのプロパティへの参照を手動で追加する必要がありました。 または、.props ファイルでプロパティを定義してから、ソリューションのすべてのプロジェクトでその .props ファイルを明示的にインポートする必要がありました。

しかし、現在ではリポジトリのルートにある Directory.Build.props という単一のファイルで新しいプロパティを定義することで、1 つのステップですべてのプロジェクトに追加できます。 MSBuild が実行されると、Microsoft.Common.props はディレクトリ構造で Directory.Build.props ファイルを検索します (また、Microsoft.Common.targets は Directory.Build.targets を探します)。 該当するものが見つかった場合、プロパティがインポートされます。 Directory.Build.props は、ディレクトリの下のプロジェクトをカスタマイズできるようにする、ユーザー定義のファイルです。

## <a name="directorybuildprops-example"></a>Directory.Build.props の例
たとえば、すべてのプロジェクトで新しい Roslyn の **/deterministic** 機能 (プロパティ `$(Deterministic)` によって Roslyn CoreCompile ターゲットで公開される) にアクセスできるようにする場合は、次のようにします。

1. リポジトリのルートに Directory.Build.props という新しいファイルを作成します。
2. そのファイルに次の XML を追加します。

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. MSBuild を実行します。 プロジェクトの既存の Microsoft.Common.props と Microsoft.Common.targets のインポートで、ファイルが検索され、インポートされます。

## <a name="search-scope"></a>検索範囲
Directory.Build.props ファイルを検索するときに、MSBuild は Directory.Build.props ファイルが見つかるまでプロジェクトの場所 ($(MSBuildProjectFullPath)) から上方向にディレクトリ構造を調べます。 たとえば、以下のディレクトリ構造のように、$(MSBuildProjectFullPath) が c:\users\username\code\test\case1 である場合、MSBuild はそこから検索を開始し、Directory.Build.props ファイルが見つかるまでディレクトリ構造を上方向に検索します。

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
ソリューション ファイルの場所は Directory.Build.props と関連はありません。

## <a name="import-order"></a>インポートの順序

Directory.Build.props は Microsoft.Common.props で最初にインポートされるため、後で定義されるプロパティを使用することはできません。 そのため、まだ定義されていない (したがって、評価が空になる) プロパティを参照しないようにしてください。

Directory.Build.targets は、NuGet パッケージから .targets ファイルがインポートされた後に Microsoft.Common.targets からインポートされます。 そのため、これを使用して、ほとんどのビルド ロジックで定義されているプロパティとターゲットをオーバーライドできますが、最後のインポートの後にプロジェクト ファイル内でカスタマイズが必要になる場合があります。

## <a name="use-case-multi-level-merging"></a>ユース ケース: マルチレベルの結合

この標準のソリューション構造が用意されているとします。

````
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
````

すべてのプロジェクト `(1)` の共通プロパティ、`src` プロジェクト `(2-src)` の共通プロパティ、`test` プロジェクト `(2-test)` の共通プロパティを用意すると便利な場合があります。

msbuild で "内" ファイル (`2-src` と `2-test`) と "外" ファイル (`1`) を正しく結合するには、msbuild で `Directory.Build.props` ファイルが見つかると後続のスキャンが停止することを考慮する必要があります。 スキャンを続行し、外ファイルに結合するには、これを両方の内ファイルに置きます。

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

msbuild の一般的手法をまとめると次のようになります。

- 特定のプロジェクトに対して、msbuild がソリューション構造の上方で最初の `Directory.Build.props` が見つけると、既定でそれを結合し、後続のスキャンを停止する
- 複数のレベルを見つけ、結合する場合、"内" ファイルから "外" ファイルを [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) する (上のコード参照)
- "外" ファイル自体でその上にある何かもインポートされない場合、そこでスキャンが停止する
- スキャン/結合プロセスを制御するには、`$(DirectoryBuildPropsPath)` と `$(ImportDirectoryBuildProps)` を使用する

もっと簡単にまとめると、何もインポートしない最初の `Directory.Build.props` が msbuild の停止箇所になります。

## <a name="see-also"></a>参照  
 [MSBuild の概念](../msbuild/msbuild-concepts.md)   
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)   
