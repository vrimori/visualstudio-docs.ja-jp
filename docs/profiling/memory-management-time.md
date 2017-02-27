---
title: "メモリ管理時間 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.paging"
helpviewer_keywords: 
  - "同時実行ビジュアライザー、ページング時間"
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# メモリ管理時間
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

タイムライン内のこれらのセグメントは、メモリ管理として分類されるブロック時間と関連付けられています。  これは、1 つのスレッドが、ページングなどメモリ管理操作と関連付けられたイベントによってブロックされていることを意味します。  この時間の間、同時実行ビジュアライザーがメモリ管理としてカウントしている API またはカーネル状態で、1 つのスレッドがブロックされています。  これには、ページングやメモリの割り当てなどのイベントが含まれます。  
  
 関連付けられた呼び出し履歴を確認し、優れたメモリ管理として分類されるブロックの原因を把握するレポートをプロファイリングを行います。  
  
## 参照  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)