---
title: デバッグ用フック関数の作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47cd3d42639785290f26d7acbbad15cd948b4f51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735522"
---
# <a name="debug-hook-function-writing"></a>デバッグ用フック関数の作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ここでは、カスタムで作成できるさまざまなデバッグ用フック関数について説明します。デバッグ用フック関数を使用すると、デバッガーが通常行う処理内部の定義済みの位置にコードを挿入できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Client ブロック用のフック関数](../debugger/client-block-hook-functions.md)  
 _CLIENT_BLOCK に格納したデータの正当性をチェックしたり、その内容を出力したりする書き込み関数について説明し、そのプロトタイプを紹介します。  
  
 [割り当てフック関数](../debugger/allocation-hook-functions.md)  
 割り当て用フック関数を定義し、そのさまざまな使用法、制限事項を紹介します。また、プロトタイプを提供します。  
  
 [割り当てフック関数と CRT メモリ割り当て](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 メモリを内部的に割り当てる C ランタイム ライブラリ関数をフック関数から呼び出す場合、`_CRT_BLOCK` 型のブロックを明示的に無視するという、割り当てフック関数の制限事項について説明します。 このトピックでは、割り当てフック関数は無視しない場合も、その結果を示します`_CRT_BLOCK`(例) を使って、ブロックと、既定の割り当てを変更する方法のフック関数、 **CrtDefaultAllocHook**します。  
  
 [レポート用のフック関数](../debugger/report-hook-functions.md)  
 `_CrtSetReportHook` について説明します。このフック関数を使用して、特定の割り当て型に関するレポートだけを選び出すことができます。 また、プロトタイプを説明します。  
  
## <a name="related-sections"></a>関連項目  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)  
 CRT デバッグ ライブラリの使用、レポート用マクロ、`malloc` と `_malloc_dbg` の相違、デバッグ用フック関数の作成、CRT デバッグ ヒープなど、C ランタイム ライブラリのデバッグ手法を説明するリンクを提供します。



