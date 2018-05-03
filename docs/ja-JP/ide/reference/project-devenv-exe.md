---
title: -Project (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2f9eef5ba7973f2735be575b6282fac0afc201c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
指定したソリューション構成内の単一のプロジェクトを、ビルド、クリーン、リビルド、または配置対象として指定します。

## <a name="syntax"></a>構文

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>引数
 /build

 `/project` `ProjName` で指定されたプロジェクトをビルドします。

 /clean

 ビルド時に作成されたすべての中間ファイルと出力ディレクトリを消去します。

 /rebuild

 `/project` `ProjName` で指定されたプロジェクトを消去してからビルドします。

 /deploy

 ビルドまたはリビルド後にプロジェクトを展開することを指定します。

 `SolnConfigName`

 必須。 `SolutionName` で指定されたソリューションに適用されるソリューション構成の名前。

 `SolutionName`

 必須。 ソリューション ファイルの完全パスと名前。

 /project `ProjName`

 任意。 ソリューション内のプロジェクト ファイルのパスと名前です。 `SolutionName` フォルダーからプロジェクト ファイルへの相対パス、プロジェクトの表示名、またはプロジェクト ファイルの完全なパスと名前を入力できます。

 /projectconfig `ProjConfigName`

 任意。 指定した `/project` に適用されるプロジェクトのビルド構成の名前。

## <a name="remarks"></a>コメント

-   `devenv /build`、/`clean`、`/rebuild`、または `/deploy` コマンドに含めて使用する必要があります。

-   空白を含む文字列を二重引用符で囲みます。

-   エラーなどのビルドの概要情報は、**[コマンド]** ウィンドウ、または `/out` スイッチで指定された任意のログ ファイルに表示できます。

## <a name="example"></a>例
 この例では、`Debug` プロジェクトのビルド構成を使用して、`MySolution` の `Debug` ソリューション構成内でプロジェクト `CSharpConsoleApp` をビルドします。

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>参照

- [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)