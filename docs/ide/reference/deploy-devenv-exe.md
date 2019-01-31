---
title: -Deploy (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /Deploy switch
- Deploy Devenv switch
- deploying applications [Visual Studio], after build
- /Deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0eef6420f09157a349658ca232a9e2551476b9d1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008479"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)

ビルドまたはリビルド後にソリューションを配置します。 マネージド コード プロジェクトにのみ適用されます。

## <a name="syntax"></a>構文

```shell
devenv SolutionName /Deploy [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>引数

- *SolutionName*

  必須です。 ソリューション ファイルの完全パスと名前。

- *SolnConfigName*

  任意。 *SolutionName* で指定されたソリューションのビルドに使用されるソリューション構成の名前 (`Debug`、`Release` など)。 複数のソリューション プラットフォームが利用できる場合、プラットフォームも指定する必要があります (`Debug|Win32` など)。 この引数が指定されていないか空の文字列 (`""`) の場合、ソリューションのアクティブな構成が使用されます。

- `/Project` *ProjName*

  任意。 ソリューション内のプロジェクト ファイルのパスと名前です。 プロジェクトの表示名または *SolutionName* フォルダーからプロジェクト ファイルへの相対パスを入力できます。 プロジェクト ファイルの完全なパスと名前を入力することもできます。

- `/ProjectConfig` *ProjConfigName*

  任意。 指定した `/Project` のビルド時に使用されるプロジェクトのビルド構成の名前 (`Debug`、`Release` など)。 複数のソリューション プラットフォームが利用できる場合、プラットフォームも指定する必要があります (`Debug|Win32` など)。 このスイッチを指定すると、*SolnConfigName* 引数はオーバーライドされます。

- `/Out` *OutputFilename*

  任意。 ツールの出力を送信する先のファイル名。 このファイルが既に存在する場合、ファイルの末尾に出力が追加されます。

## <a name="remarks"></a>コメント

指定するプロジェクトは、配置プロジェクトである必要があります。 指定したプロジェクトが配置プロジェクトでない場合に、ビルド済みのプロジェクトを渡して配置しようとすると、エラーが発生して配置は失敗します。

空白を含む文字列を二重引用符で囲みます。

エラーなどのビルドの概要情報は、**[コマンド]** ウィンドウ、または [/Out](out-devenv-exe.md) スイッチで指定された任意のログ ファイルに表示できます。

## <a name="example"></a>例

この例では、`MySolution` 内の `Release` プロジェクト ビルド構成を使用して、プロジェクト `CSharpWinApp` を配置します。

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>関連項目

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)