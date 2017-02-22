---
title: "GPU アクティビティ (他のプロセス) | Microsoft Docs"
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
  - "vs.cv.threads.timeline.gpuother"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# GPU アクティビティ (他のプロセス)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

同時実行ビジュアライザーのスレッド ビューの **\[GPU のアクティビティ \(他のプロセス\) \]** セグメントは GPU がシステム上の他のプロセスによって要求を処理したときを表します。  これらの要求は、メモリ アクセス \(DMA\) の直接パケットとして GPU に送信されます。セグメントの長さはパケットが GPU によって処理された期間を表します。  
  
 この種のセグメントを選択すると、**\[現在\]** タブのレポートが処理されたパケットに関する情報を表示します。情報はパケットがパケットを送信した、パケットを処理するために要する時間関連付けられた DirectX エンジン、プロセスとハードウェア キューで待機していた時間が含まれます。