---
title: "GPU アクティビティ (このプロセス) | Microsoft Docs"
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
  - "vs.cv.threads.timeline.gpuexecution"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# GPU アクティビティ (このプロセス)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

同時実行ビジュアライザーのスレッド ビューの **\[GPU のアクティビティ \(このプロセス\) \]** セグメントは GPU を現在のプロセスに代わって要求を処理したときを表します。  これらの要求は、メモリ アクセス \(DMA\) の直接パケットとして GPU に送信されます。  セグメントの長さは GPU を現在のプロセスに代わって DMA パケットを処理していた時間を示します。  
  
 GPU アクティビティ セグメントを選択すると、**\[現在\]** タブのレポートが処理された DMA パケットに関する情報を表示します。  この情報はパケットがパケットを送信した、パケットを処理するために要する時間関連付けられた DirectX エンジン、プロセスとハードウェア キューで待機していた時間が含まれます。  現在のプロセスの外部のプロセスは GPU に物理的に DMA パケットをすることがあります。  同時実行ビジュアライザーは、別のプロセスが現在のプロセスに代わって GPU に作業をいつ送信したことを検出できます。