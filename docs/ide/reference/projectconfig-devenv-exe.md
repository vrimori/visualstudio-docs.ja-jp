---
title: DevEnv ProjectConfig スイッチ
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44f5d4479658b450074ba35f2759a273bb584e0a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764655"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

**/project** 引数で指定されたプロジェクトをビルド、消去、リビルド、または展開する際に適用されるプロジェクトのビルド構成を指定します。

## <a name="syntax"></a>構文

```cmd
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>引数

|||
|-|-|
|/build|**/project** 引数で指定されたプロジェクトをビルドします。|
|/clean|ビルド時に作成されたすべての中間ファイルと出力ディレクトリを消去します。|
|/rebuild|**/project** 引数で指定されたプロジェクトを消去してからビルドします。|
|/deploy|ビルドまたはリビルド後にプロジェクトを展開することを指定します。|
|*SolnConfigName*|必須。 *SolutionName* で指定されたソリューションに適用されるソリューション構成の名前。 複数のソリューション プラットフォームが利用できる場合、**"Debug\|Win32"** など、プラットフォームも指定する必要があります。|
|*SolutionName*|必須。 ソリューション ファイルの完全パスと名前。|
|/project *ProjName*|任意。 ソリューション内のプロジェクト ファイルのパスと名前です。 *SolutionName* フォルダーからプロジェクト ファイルへの相対パス、プロジェクトの表示名、プロジェクト ファイルの完全なパスと名前を入力できます。|
|/projectconfig *ProjConfigName*|任意。 **/project** 引数で指定されたプロジェクトに適用されるプロジェクトのビルド構成の名前。 複数のソリューション プラットフォームが利用できる場合、**"Debug\|Win32"** など、プラットフォームも指定する必要があります。|

## <a name="remarks"></a>コメント

**/projectconfig** スイッチは、**/build**、**/clean**、**/rebuild**、**/deploy** コマンドの一部として **/project** スイッチと共に使用する必要があります。

空白を含む文字列を二重引用符で囲みます。

エラーなどのビルドの概要情報は、[コマンド] ウィンドウ、または **/out** スイッチで指定された任意のログ ファイルに表示できます。

## <a name="example"></a>例

次のコマンドでは、"MySolution" の "Debug" ソリューション構成内の "Debug" プロジェクト ビルド構成を使用し、プロジェクト "CSharpConsoleApp" がビルドされます。

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>関連項目

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)