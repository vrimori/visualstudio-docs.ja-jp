---
title: デバッグ用フック関数の作成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9218c36f550c61484054d180ecb4dccb1ca53f3d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947505"
---
# <a name="debug-hook-function-writing"></a>デバッグ用フック関数の作成
ここでは、カスタムで作成できるさまざまなデバッグ用フック関数について説明します。デバッグ用フック関数を使用すると、デバッガーが通常行う処理内部の定義済みの位置にコードを挿入できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Client ブロック用のフック関数](../debugger/client-block-hook-functions.md)  
 _CLIENT_BLOCK に格納したデータの正当性をチェックしたり、その内容を出力したりする書き込み関数について説明し、そのプロトタイプを紹介します。  
  
 [割り当てフック関数](../debugger/allocation-hook-functions.md)  
 割り当て用フック関数を定義し、そのさまざまな使用法、制限事項を紹介します。また、プロトタイプを提供します。  
  
 [割り当てフック関数と C ランタイムのメモリ割り当て](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 メモリを内部的に割り当てる C ランタイム ライブラリ関数をフック関数から呼び出す場合、`_CRT_BLOCK` 型のブロックを明示的に無視するという、割り当てフック関数の制限事項について説明します。 また、割り当てフック関数が `_CRT_BLOCK` ブロックを無視しない場合の結果を例と共に示し、既定の割り当てフック関数 **CrtDefaultAllocHook** を変更する方法について説明します。  
  
 [レポート用のフック関数](../debugger/report-hook-functions.md)  
 `_CrtSetReportHook` について説明します。このフック関数を使用して、特定の割り当て型に関するレポートだけを選び出すことができます。 また、プロトタイプを説明します。  
  
## <a name="related-sections"></a>関連項目  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)  
 CRT デバッグ ライブラリの使用、レポート用マクロ、`malloc` と `_malloc_dbg` の相違、デバッグ用フック関数の作成、CRT デバッグ ヒープなど、C ランタイム ライブラリのデバッグ手法を説明するリンクを提供します。