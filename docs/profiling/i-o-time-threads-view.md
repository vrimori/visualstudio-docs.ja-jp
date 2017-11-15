---
title: "I/O 時間 (スレッド ビュー) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.io
helpviewer_keywords: Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d53cfcf4daa5e1ac1129230884684692867b121d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="io-time-threads-view"></a>I/O 時間 (スレッド ビュー)
タイムライン内のこれらのセグメントは、I/O として分類されたブロック時間に関連付けられます。 つまり、スレッドは I/O 操作の完了を待ちます。 スレッドは API でブロックされている可能性があります。あるいは、同時実行ビジュアライザーが I/O としてカウントしている I/O 関連のカーネル待機によりブロックされている可能性があります。 `CreateFile()`、`ReadFile()`、`WSARecv()` のような API がこのグループに属します。  
  
## <a name="see-also"></a>関連項目  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)