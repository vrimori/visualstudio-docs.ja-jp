---
title: QuickWatch コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8e4ebd4ee4de8cd15a8ec930c200e7224da2186
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837447"
---
# <a name="quick-watch-command"></a>QuickWatch コマンド
選択または指定したテキストが [[クイック ウォッチ]](../../debugger/watch-and-quickwatch-windows.md) ウィンドウの [式] フィールドに表示されます。 このダイアログ ボックスを利用し、デバッガーが認識する変数または式の現在値やレジスタのコンテンツの現在値を計算できます。 さらに、非定数の変数の値やレジストリのコンテンツの値を変更できます。

## <a name="syntax"></a>構文

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>引数
 `text`

 任意。 **[クイック ウォッチ]** ダイアログ ボックスに追加するテキスト。

## <a name="remarks"></a>コメント
 `text` を省略した場合、カーソルで現在選択されているテキストや単語がウォッチ ウィンドウに追加されます。

## <a name="example"></a>例

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>「

- [Visual Studio でウォッチ ウィンドウとクイック ウォッチ ウィンドウを使用して変数のウォッチ ポイントを設定する](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)