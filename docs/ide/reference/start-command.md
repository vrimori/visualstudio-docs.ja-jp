---
title: Start コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1e5ade7d02882633504ac5615ee751b2533adde
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="start-command"></a>Start コマンド
スタートアップ プロジェクトのデバッグを開始します。

## <a name="syntax"></a>構文

```
Debug.Start [address]
```

## <a name="arguments"></a>引数
 `address`

 任意。 プログラムの実行を中断するアドレス。ソース コードでのブレークポイントに似ています。 この引数は、デバッグ モードでのみ有効です。

## <a name="remarks"></a>コメント
 **Start** コマンドを実行すると、指定したアドレスまで RunToCursor 操作が実行されます。

## <a name="example"></a>例
 この例では、デバッガーを起動し、発生した例外はすべて無視されます。

```
>Debug.Start
```

## <a name="see-also"></a>参照

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)