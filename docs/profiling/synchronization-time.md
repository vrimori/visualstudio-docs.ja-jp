---
title: "同期時間 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.synchronization"
helpviewer_keywords: 
  - "同時実行ビジュアライザー, 同期時間"
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 同期時間
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

タイムライン内のこれらのセグメントは、同期として分類されるブロック時間と関連付けられています。  同期でスレッドにブロックされたマークが付いている場合、次のいずれかを示しています。  
  
-   スレッドの実行が、`EnterCriticalSection()` または `WaitForSingleObject()` などの既知のスレッド同期 API を呼び出す結果になった可能性がある。  
  
-   API 照合アルゴリズムが全体として包括的にならず、そのために、他のカテゴリにマップされている可能性がある一部の API も同期として表示されている可能性がある。呼び出し履歴内のフレームの最終的な到達先が、このカテゴリにマップされた、基になるカーネルをブロックしている基本要素である場合にこの状態になります。  
  
 スレッドをブロックしたイベントの根本的な原因を理解するには、ブロックしている呼び出し履歴とプロファイル レポートをよく調べてください。  
  
## 参照  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)