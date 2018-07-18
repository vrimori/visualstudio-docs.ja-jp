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
ms.openlocfilehash: bbd2d64d8103afe1e303052c9b27fc2cc85cab58
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704695"
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

## <a name="see-also"></a>参照

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)