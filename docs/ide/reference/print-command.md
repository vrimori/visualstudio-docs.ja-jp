---
title: Print コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31f604d6df45cb22d18401b5925867d5ab0e02b8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900887"
---
# <a name="print-command"></a>Print コマンド
式を評価するか、指定したテキストを表示します。

## <a name="syntax"></a>構文

```cmd
Debug.Print text
```

## <a name="arguments"></a>引数
 `text`

 必須です。 評価対象の式または表示対象のテキストです。

## <a name="remarks"></a>コメント
 このコマンドのエイリアスとして疑問符 (?) を使用できます。 したがって、たとえば次のコマンド

```cmd
>Debug.Print expA
```

 は、次のように記述することもできます。

```cmd
>? expA
```

 どちらのコマンドでも、式 `expA` の現在の値が返されます。

## <a name="example"></a>例

```cmd
>Debug.Print varA
```

## <a name="see-also"></a>「

- [Evaluate Statement コマンド](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)