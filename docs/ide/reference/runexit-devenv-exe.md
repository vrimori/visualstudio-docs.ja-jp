---
title: -Runexit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fa715c97310edc447610b0c0ae61226ab5334f9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955121"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
指定したプロジェクトまたはソリューションをコンパイルおよび実行してから、統合開発環境 (IDE) を閉じます。

## <a name="syntax"></a>構文

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>引数
 `SolutionName`

 必須です。 ソリューション ファイルの完全パスと名前。

 `ProjectName`

 必須です。 プロジェクト ファイルの完全パスと名前。

## <a name="remarks"></a>コメント
 アクティブなソリューション構成に対して指定された設定に従って、指定したプロジェクトまたはソリューションをコンパイルして実行します。 このスイッチはプロジェクトまたはソリューションの実行中に IDE を最小化し、プロジェクトまたはソリューションの実行の完了後に IDE を閉じます。

-   空白を含む文字列を二重引用符で囲みます。

-   エラーなどの概要情報は、**[コマンド]** ウィンドウ、または `/out`スイッチで指定した任意のログ ファイルに表示できます。

## <a name="example"></a>例
 この例では、アクティブな配置構成を使用し、IDE を最小化した状態でソリューション `MySolution` を実行してから IDE を閉じます。

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>「

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)