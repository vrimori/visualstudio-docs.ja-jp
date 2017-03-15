---
title: "デバッグ用フック関数の作成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "デバッグ用フック関数"
  - "デバッグ [C++], CRT デバッグ サポート"
  - "デバッグ [CRT], デバッグ用フック関数"
  - "フック"
  - "フック, デバッグ"
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# デバッグ用フック関数の作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、カスタムで作成できるさまざまなデバッグ用フック関数について説明します。デバッグ用フック関数を使用すると、デバッガーが通常行う処理内部の定義済みの位置にコードを挿入できます。  
  
## このセクションの内容  
 [Client ブロック用のフック関数](../debugger/client-block-hook-functions.md)  
 \_CLIENT\_BLOCK に格納したデータの正当性をチェックしたり、その内容を出力したりする書き込み関数について説明し、そのプロトタイプを紹介します。  
  
 [割り当てフック関数](../debugger/allocation-hook-functions.md)  
 割り当て用フック関数を定義し、そのさまざまな使用法、制限事項を紹介します。また、プロトタイプを提供します。  
  
 [割り当てフック関数と C ランタイムのメモリ割り当て](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 メモリを内部的に割り当てる C ランタイム ライブラリ関数をフック関数から呼び出す場合、`_CRT_BLOCK` 型のブロックを明示的に無視するという、割り当てフック関数の制限事項について説明します。  また、割り当てフック関数が `_CRT_BLOCK` ブロックを無視しない場合の結果を例と共に示し、既定の割り当てフック関数 **CrtDefaultAllocHook** を変更する方法について説明します。  
  
 [レポート用のフック関数](../debugger/report-hook-functions.md)  
 `_CrtSetReportHook` について説明します。このフック関数を使用して、特定の割り当て型に関するレポートだけを選び出すことができます。  また、プロトタイプを説明します。  
  
## 関連項目  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)  
 CRT デバッグ ライブラリの使用、レポート用マクロ、`malloc` と `_malloc_dbg` の相違、デバッグ用フック関数の作成、CRT デバッグ ヒープなど、C ランタイム ライブラリのデバッグ手法を説明するリンクを提供します。