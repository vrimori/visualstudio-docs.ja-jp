---
title: Evaluate Statement コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89f8eacc11e591545e1a542c0e1eeda3c45b7df3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002393"
---
# <a name="evaluate-statement-command"></a>Evaluate Statement コマンド
指定したステートメントを評価し、表示します。

## <a name="syntax"></a>構文

```cmd
Debug.EvaluateStatement text
```

## <a name="arguments"></a>引数
 `text` 必須。 評価するステートメント。

## <a name="remarks"></a>コメント
 **EvaluateStatement** コマンドをどのウィンドウに入力するかによって、等号 (=) を比較演算子として解釈するのか、代入演算子として解釈するのかが決まります。

 **[コマンド]** ウィンドウの場合、等号 (=) は、比較演算子と解釈されます。 したがって、たとえば変数 `a` と変数 `b` の値が異なる場合、次のコマンド

```cmd
>Debug.EvaluateStatement(a=b)
```

 は、値 `false` を返します。

 一方、**[イミディエイト]** ウィンドウの場合、等号 (=) は、代入演算子と解釈されます。 したがって、たとえば次のコマンド

```cmd
>Debug.EvaluateStatement(a=b)
```

 では、変数 `a` に変数 `b` の値が代入されます。

## <a name="example"></a>例

```cmd
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>「

- [Print コマンド](../../ide/reference/print-command.md)
- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)