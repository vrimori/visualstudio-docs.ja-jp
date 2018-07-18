---
title: -Deploy (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 368680321f8ff8ab908e79e075a5797ba9ecd598
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945117"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
ビルドまたはリビルド後にソリューションを配置します。 マネージ コード プロジェクトにのみ適用されます。

## <a name="syntax"></a>構文

```
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]
```

## <a name="arguments"></a>引数
 `SolnConfigName`

 必須。 `SolutionName` で指定されたソリューションのビルドに使用されるソリューション構成の名前。

 `SolutionName`

 必須。 ソリューション ファイルの完全パスと名前。

 /project `ProjName`

 任意。 ソリューション内のプロジェクト ファイルのパスと名前です。 `SolutionName` フォルダーからプロジェクト ファイルへの相対パス、プロジェクトの表示名、またはプロジェクト ファイルの完全なパスと名前を入力できます。

 /projectconfig `ProjConfigName`

 任意。 指定した `/project` のビルド時に使用されるプロジェクトのビルド構成の名前。

## <a name="remarks"></a>コメント
 指定するプロジェクトは、配置プロジェクトである必要があります。 指定したプロジェクトが配置プロジェクトでない場合に、ビルド済みのプロジェクトを渡して配置しようとすると、エラーが発生して配置は失敗します。

 空白を含む文字列を二重引用符で囲みます。

 エラーなどのビルドの概要情報は、**[コマンド]** ウィンドウ、または `/out` スイッチで指定された任意のログ ファイルに表示できます。

## <a name="example"></a>例
 この例では、`Release` プロジェクトのビルド構成を使用して、`MySolution` の `Release` ソリューション構成内でプロジェクト `CSharpConsoleApp` を配置します。

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>参照

- [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)