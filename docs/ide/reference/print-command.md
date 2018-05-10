---
title: Print コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
ms.openlocfilehash: 2ef4f0c5c6bd5be2820e1f666529fc43fac59763
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="print-command"></a>Print コマンド
式を評価するか、指定したテキストを表示します。

## <a name="syntax"></a>構文

```cmd
Debug.Print text
```

## <a name="arguments"></a>引数
 `text`

 必須。 評価対象の式または表示対象のテキストです。

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

## <a name="see-also"></a>参照

- [Evaluate Statement コマンド](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)