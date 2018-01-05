---
title: "デバッグ用フック関数の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.hooks
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
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b5071e2fd7c8114cb13697eef4a4ddfa32d95718
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="debug-hook-function-writing"></a>デバッグ用フック関数の作成
ここでは、カスタムで作成できるさまざまなデバッグ用フック関数について説明します。デバッグ用フック関数を使用すると、デバッガーが通常行う処理内部の定義済みの位置にコードを挿入できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Client ブロック用のフック関数](../debugger/client-block-hook-functions.md)  
 _CLIENT_BLOCK に格納したデータの正当性をチェックしたり、その内容を出力したりする書き込み関数について説明し、そのプロトタイプを紹介します。  
  
 [割り当てフック関数](../debugger/allocation-hook-functions.md)  
 割り当て用フック関数を定義し、そのさまざまな使用法、制限事項を紹介します。また、プロトタイプを提供します。  
  
 [割り当てフック関数と CRT メモリ割り当て](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 メモリを内部的に割り当てる C ランタイム ライブラリ関数をフック関数から呼び出す場合、`_CRT_BLOCK` 型のブロックを明示的に無視するという、割り当てフック関数の制限事項について説明します。 このトピックの内容も一覧表示されます、ような影響場合は、割り当てフック関数は無視されません`_CRT_BLOCK`(例) を使って、ブロックおよび既定の割り当てを変更する方法のフック関数、 **CrtDefaultAllocHook**です。  
  
 [レポート用のフック関数](../debugger/report-hook-functions.md)  
 `_CrtSetReportHook` について説明します。このフック関数を使用して、特定の割り当て型に関するレポートだけを選び出すことができます。 また、プロトタイプを説明します。  
  
## <a name="related-sections"></a>関連項目  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)  
 CRT デバッグ ライブラリの使用、レポート用マクロ、`malloc` と `_malloc_dbg` の相違、デバッグ用フック関数の作成、CRT デバッグ ヒープなど、C ランタイム ライブラリのデバッグ手法を説明するリンクを提供します。