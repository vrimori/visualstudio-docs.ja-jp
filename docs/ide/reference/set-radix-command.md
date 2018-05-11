---
title: SetRadix コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c18d825ae61dd80ab7b72e1e14c7dc3412582317
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="set-radix-command"></a>SetRadix コマンド
整数値を表示するために使用する基数値を設定または返します。

## <a name="syntax"></a>構文

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>引数
 `10` または `16`、あるいは `hex` または `dec`

 任意。 10 (10 または dec) 進数または 16 (16 または hex) 進数を示します。 引数を省略すると、現在の基数値が返されます。

## <a name="example"></a>例
 この例では、整数値を 16 進形式で表示するための環境を設定します。

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>参照

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)