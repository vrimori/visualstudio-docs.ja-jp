---
title: ビルドのカスタマイズ | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9aa56cf0d0ae6d715685ee331cd60c95eedc5c60
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945976"
---
# <a name="customize-your-build"></a>ビルドのカスタマイズ

標準のビルド プロセス (*Microsoft.Common.props* と *Microsoft.Common.targets* のインポート) を使用する MSBuild プロジェクトには、ビルド プロセスのカスタマイズに使用できる拡張フックがいくつかあります。

## <a name="adding-arguments-to-command-line-msbuild-invocations-for-your-project"></a>プロジェクトのコマンドライン MSBuild 呼び出しに引数を追加する

ソース ディレクトリの中またはその上にある *Directory.Build.rsp* ファイルがプロジェクトのコマンドライン ビルドに適用されます。 詳細については、「[MSBuild 応答ファイル](../msbuild/msbuild-response-files.md#directorybuildrsp)」を参照してください。

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props と Directory.Build.targets

MSBuild バージョン 15 より前では、ソリューション内のプロジェクトに新しいカスタム プロパティを提供する場合、ソリューション内のすべてのプロジェクト ファイルにそのプロパティへの参照を手動で追加する必要がありました。 または、*.props* ファイルでプロパティを定義してから、ソリューションのすべてのプロジェクトでその *.props* ファイルを明示的にインポートする必要がありました。

ただし、現在では、ソースが含まれるルート フォルダーにある *Directory.Build.props* という単一のファイルで新しいプロパティを定義することで、1 つのステップですべてのプロジェクトに追加できます。 MSBuild が実行されると、*Microsoft.Common.props* はディレクトリ構造で *Directory.Build.props* ファイルを検索します (また、*Microsoft.Common.targets* は *Directory.Build.targets* を探します)。 該当するものが見つかった場合、プロパティがインポートされます。 *Directory.Build.props* は、ディレクトリの下のプロジェクトをカスタマイズできるようにする、ユーザー定義のファイルです。

### <a name="directorybuildprops-example"></a>Directory.Build.props の例

たとえば、すべてのプロジェクトで新しい Roslyn の **/deterministic** 機能 (プロパティ `$(Deterministic)` によって Roslyn `CoreCompile` ターゲットで公開される) にアクセスできるようにする場合は、次のようにします。

1. リポジトリのルートに *Directory.Build.props* という新しいファイルを作成します。
2. そのファイルに次の XML を追加します。

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. MSBuild を実行します。 プロジェクトの既存の *Microsoft.Common.props* と *Microsoft.Common.targets* のインポートで、ファイルが検索され、インポートされます。

### <a name="search-scope"></a>検索範囲

*Directory.Build.props* ファイルを検索するときに、MSBuild は *Directory.Build.props* ファイルが見つかるまでプロジェクトの場所 (`$(MSBuildProjectFullPath)`) から上方向にディレクトリ構造を調べます。 たとえば、以下のディレクトリ構造のように、`$(MSBuildProjectFullPath)` が *c:\users\username\code\test\case1* である場合、MSBuild はそこから検索を開始し、*Directory.Build.props* ファイルが見つかるまでディレクトリ構造を上方向に検索します。

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

ソリューション ファイルの場所は *Directory.Build.props* と関連はありません。

### <a name="import-order"></a>インポートの順序

*Directory.Build.props* は *Microsoft.Common.props* で最初にインポートされ、後で定義されるプロパティを使用することはできません。 そのため、まだ定義されていない (したがって、評価が空になる) プロパティを参照しないようにしてください。

*Directory.Build.targets* は、NuGet パッケージから *.targets* ファイルがインポートされた後に *Microsoft.Common.targets* からインポートされます。 そのため、ほとんどのビルド ロジックで定義されているプロパティとターゲットをオーバーライドできますが、最後のインポートの後でプロジェクト ファイルのカスタマイズが必要になる場合があります。

### <a name="use-case-multi-level-merging"></a>ユース ケース: マルチレベルの結合

この標準のソリューション構造が用意されているとします。

```
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
```

すべてのプロジェクト *(1)* の共通プロパティ、*src* プロジェクト *(2-src)* の共通プロパティ、*test* プロジェクト *(2-test)* の共通プロパティを用意すると便利な場合があります。

MSBuild で "内" ファイル (*2-src* と *2-test*) と "外" ファイル (*1*) を正しく結合するには、MSBuild で *Directory.Build.props* ファイルが見つかると後続のスキャンが停止することを考慮する必要があります。 スキャンを続行し、外ファイルに結合するには、次のコードを両方の内ファイルに追加します。

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

MSBuild の一般的手法をまとめると次のようになります。

- 特定のプロジェクトに対して、MSBuild がソリューション構造の上方で最初の *Directory.Build.props* が見つけると、既定でそれを結合し、後続のスキャンを停止する
- 複数のレベルを見つけ、結合する場合、"内" ファイルから "外" ファイルを [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) する (上のコード参照)
- "外" ファイル自体でその上にある何かもインポートされない場合、そこでスキャンが停止する
- スキャン/結合プロセスを制御するには、`$(DirectoryBuildPropsPath)` と `$(ImportDirectoryBuildProps)` を使用する

もっと簡単にまとめると、何もインポートしない最初の *Directory.Build.props* が MSBuild の停止箇所になります。

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

既定では、*Microsoft.Common.props* は `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` をインポートし、*Microsoft.Common.targets* は `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets` をインポートします。 `MSBuildProjectExtensionsPath` の既定値は `$(BaseIntermediateOutputPath)`、`obj/` です。 NuGet はこのメカニズムを使って、パッケージに付随するビルド ロジックを参照します。つまり、復元時、パッケージの内容を参照する `{project}.nuget.g.props` ファイルが作成されます。

*Directory.Build.props* において、または *Microsoft.Common.props* をインポートする前に、`ImportProjectExtensionProps` プロパティを `false` に設定することによって、この拡張メカニズムを無効にできます。

> [!NOTE]
> MSBuildProjectExtensionsPath インポートを無効にすると、NuGet パッケージ付属のビルド ロジックがプロジェクトに適用されなくなります。 一部の NuGet パッケージでは、その機能を実行するためにビルド ロジックが必要であり、このインポートが無効になると役に立たなくなります。

## <a name="user-file"></a>.user ファイル

*Microsoft.Common.CurrentVersion.targets* では、存在する場合は `$(MSBuildProjectFullPath).user` がインポートされます。この追加拡張子でプロジェクトの隣にファイルを作成できます。 ソース管理にチェックインする予定の長期的な変更の場合、プロジェクト自体の変更をお勧めします。将来、保守管理を担当する人はこの拡張メカニズムについて知る必要がありません。

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath と MSBuildUserExtensionsPath

> [!WARNING]
> これらの拡張メカニズムを使用すると、コンピューター間で繰り返し可能なビルドを得ることが難しくなります。 ソース管理システムにチェックインし、コードベースのすべての開発者の間で共有できる構成を使用してみてください。

慣例的に、多くのコア ビルド ロジック ファイルでは、

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

そのコンテンツの前、および

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

後にインポートします。 インストールされた SDK で、共通プロジェクト タイプのビルド ロジックを拡張できます。

同じディレクトリ構造が `$(MSBuildUserExtensionsPath)` で検索されます。これはユーザー別フォルダー *%LOCALAPPDATA%\Microsoft\MSBuild* です。 そのフォルダーに置かれたファイルは、そのユーザーの資格情報の下で実行される、該当するプロジェクト タイプのすべてのビルドでインポートされます。 このユーザー拡張は、パターン `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}` でインポート ファイルに基づいて名前が付けられたプロパティを設定することで無効にできます。 たとえば、`ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` を `false` に設定すると、`$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*` がインポートされません。

## <a name="customizing-the-solution-build"></a>ソリューション ビルドをカスタマイズする

> [!IMPORTANT]
> この方法によるソリューション ビルドのカスタマイズは、*MSBuild.exe* を持つコマンドライン ビルドにのみ適用されます。 Visual Studio 内のビルドには適用**されません**。

MSBuild でソリューション ファイルがビルドされるとき、最初に内部でプロジェクト ファイルに変換され、それからビルドされます。 生成されたプロジェクト ファイルは、ターゲットを定義する前に `before.{solutionname}.sln.targets` をインポートし、ターゲットをインポートした後に `after.{solutionname}.sln.targets` をインポートします。ターゲットには、`$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` ディレクトリと `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` ディレクトリにインストールされたターゲットが含まれます。

たとえば、次のコードを含む *after.MyCustomizedSolution.sln.targets* という名前の同じディレクトリにファイルを作成することで、*MyCustomizedSolution.sln* のビルド後にカスタム ログ メッセージを書き込む新しいターゲットを定義できます。

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="see-also"></a>関連項目

[MSBuild の概念](../msbuild/msbuild-concepts.md)

[MSBuild リファレンス](../msbuild/msbuild-reference.md)
