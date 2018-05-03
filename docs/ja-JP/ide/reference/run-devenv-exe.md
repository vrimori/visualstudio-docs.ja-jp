---
title: -Run (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b784b794945363afb2ea8955b5ad1bde96c36528
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
指定したプロジェクトまたはソリューションをコンパイルして実行します。

## <a name="syntax"></a>構文

```
devenv {/run|/r} {SolutionName|ProjectName}
```

## <a name="arguments"></a>引数
 `SolutionName`

 必須。 ソリューション ファイルの完全パスと名前。

 `ProjectName`

 必須。 プロジェクト ファイルの完全パスと名前。

## <a name="remarks"></a>コメント
 アクティブなソリューション構成に対して指定された設定に従って、指定したプロジェクトまたはソリューションをコンパイルして実行します。 このスイッチは、統合開発環境 (IDE) を起動し、プロジェクトまたはソリューションの実行が完了しても IDE をアクティブな状態のままにします。

-   空白を含む文字列を二重引用符で囲みます。

-   エラーなどの概要情報は、**[コマンド]** ウィンドウ、または `/out`スイッチで指定した任意のログ ファイルに表示できます。

## <a name="example"></a>例
 この例では、アクティブな配置構成を使用して、ソリューション `MySolution` を実行します。

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>参照

- [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)