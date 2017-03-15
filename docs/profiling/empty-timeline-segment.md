---
title: "空のタイムライン セグメントです | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.empty"
helpviewer_keywords: 
  - "同時実行ビジュアライザー, 空のタイムライン セグメント"
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 空のタイムライン セグメントです
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

同時実行ビジュアライザーでは、タイムラインのあるセクションが空である理由にチャネルの種類によって白い背景が異なります\) です。  
  
-   CPU のスレッド チャネルで、スレッドはタイムラインのこの部分の間にないことを意味します。  スレッドを目的とする場合は、ズーム コントロールまたは水平方向にスクロールを使用して実行セクションを検索できます。  
  
-   I\/O チャネルで、ディスク アクセスが時間のターゲット プロセスに代わって場合に実行されなかったことを意味します。  
  
-   DirectX チャネルで、GPU 作業はタイムラインのこの部分の間にターゲット プロセスの代わりに実行されなかったことを意味します。  
  
-   マーカー チャネルで、マーカーが生成されなかったことを意味します。  
  
## 参照  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)   
 [ズーム コントロール \(スレッド ビュー\)](../profiling/zoom-control-threads-view.md)