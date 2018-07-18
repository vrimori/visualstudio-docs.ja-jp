---
title: ToggleBreakpoint コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14f4d60bcbf7c7f394d62cc881c78ef9aa51e545
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946807"
---
# <a name="toggle-breakpoint-command"></a>ToggleBreakpoint コマンド
ファイル内の現在位置で、現在の状態に基づいてブレークポイントのオン/オフを切り替えます。

## <a name="syntax"></a>構文

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>引数
 `text` 省略可能。 テキストを指定すると、行が名前付きのブレークポイントとしてマークされます。 それ以外の場合は、行は名前のないブレークポイントとしてマークされ、これは F9 キーを押したときの動作に似ています。

## <a name="example"></a>例
 次の例では、現在のブレークポイントを切り替えます。

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>参照

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)