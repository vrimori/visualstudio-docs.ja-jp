---
title: "ビルドのカスタマイズ | Microsoft Docs"
ms.custom: 
ms.date: 06/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: 86f7fef0365a47e8ea88bc3fc46cb0016efd4628
ms.contentlocale: ja-jp
ms.lasthandoff: 06/15/2017

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

## <a name="see-also"></a>関連項目  
 [MSBuild の概念](../msbuild/msbuild-concepts.md)   
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)   

