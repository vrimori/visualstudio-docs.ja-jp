---
title: ListThreads コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1a914ffcd242626b0f519ab541c4c381a4597da
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846140"
---
# <a name="list-threads-command"></a>ListThreads コマンド
現在のプログラムのスレッド一覧を表示します。

## <a name="syntax"></a>構文

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>引数
 `index`

 任意。 スレッドをインデックスで選択して、現在のスレッドにします。

## <a name="remarks"></a>コメント
 指定した場合、`index` 引数により、示されたスレッドが現在のスレッドとしてマークされます。 一覧の現在のスレッドの横にはアスタリスク (*) が表示されます。

## <a name="example"></a>例

```
>Debug.ListThreads
```

## <a name="see-also"></a>「

- [ListCallStack コマンド](../../ide/reference/list-call-stack-command.md)
- [ListDisassembly コマンド](../../ide/reference/list-disassembly-command.md)
- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)