---
title: Start コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0307bc8fef348aa408bf6d4fad53759df61806fb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962824"
---
# <a name="start-command"></a>Start コマンド
スタートアップ プロジェクトのデバッグを開始します。

## <a name="syntax"></a>構文

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>引数
 `address`

 任意。 プログラムの実行を中断するアドレス。ソース コードでのブレークポイントに似ています。 この引数は、デバッグ モードでのみ有効です。

## <a name="remarks"></a>コメント
 **Start** コマンドを実行すると、指定したアドレスまで RunToCursor 操作が実行されます。

## <a name="example"></a>例
 この例では、デバッガーを起動し、発生した例外はすべて無視されます。

```cmd
>Debug.Start
```

## <a name="see-also"></a>「

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)