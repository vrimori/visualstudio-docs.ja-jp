---
title: -Rebuild (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 782a0864c692d8c50932f41077762c994f24eeae
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985684"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
指定したソリューション構成を消去してからビルドします。

## <a name="syntax"></a>構文

```cmd
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>引数
 `SolnConfigName`

 必須です。 `SolutionName` で指定されたソリューションのリビルドに使用されるソリューション構成の名前。

 `SolutionName`

 必須です。 ソリューション ファイルの完全パスと名前。

 /project `ProjName`

 任意。 ソリューション内のプロジェクト ファイルのパスと名前です。 `SolutionName` フォルダーからプロジェクト ファイルへの相対パス、プロジェクトの表示名、またはプロジェクト ファイルの完全なパスと名前を入力できます。

 /projectconfig `ProjConfigName`

 任意。 指定した `/project` のリビルド時に使用されるプロジェクトのビルド構成の名前。

## <a name="remarks"></a>コメント

-   このスイッチは、統合開発環境 (IDE) 内の **[ソリューションのリビルド]** メニュー コマンドと同じ機能を実行します。

-   空白を含む文字列を二重引用符で囲みます。

-   エラーを含むクリーンとビルドの概要情報は、**[コマンド]** ウィンドウ、または `/out` スイッチで指定された任意のログ ファイルに表示できます。

## <a name="example"></a>例
 この例では、`Debug` プロジェクトのビルド構成を使用して、`MySolution` の `Debug` ソリューション構成内でプロジェクト `CSharpWinApp` を消去してリビルドします。

```cmd
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>「

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)