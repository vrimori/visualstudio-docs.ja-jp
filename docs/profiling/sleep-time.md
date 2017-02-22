---
title: "スリープ時間 | Microsoft Docs"
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
  - "vs.cv.threads.timeline.sleep"
helpviewer_keywords: 
  - "同時実行ビジュアライザー, スリープ時間"
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# スリープ時間
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

タイムライン内のこれらのセグメントは、スリープとして分類されるブロック時間と関連付けられています。  スリープのカテゴリは、1 つのスレッドが自発的にその論理コアを明け渡して、処理を行わなかったことを示しています。  この時間の間、同時実行ビジュアライザーがスリープとしてカウントしている API で、1 つのスレッドがブロックされています。  `Sleep()` や `SwitchToThread()` などの API がこのグループになります。  
  
## 参照  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)