---
title: "現在のタブ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.reportnav.current"
helpviewer_keywords: 
  - "同時実行ビジュアライザー、選択位置の呼び出し履歴"
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 現在のタブ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**\[現在\]** タブをクリックして、CPU のスレッド セグメントを選択するタイムライン内で現在選択されている位置に最も近い呼び出し履歴を参照できます \(存在する場合\)。この場合、選択位置は、タイムラインの上に黒の矢印 \(キャレット\) でも表されます。  ブロッキング セグメントを選択した場合、キャレットは実行されなかったため表示されません。  ただし、そのセグメントは強調表示され、呼び出し履歴が表示されます。  
  
 **\[現在\]** タブは、DirectX アクティビティ セグメント、マーカーと I\/O アクセスに関する情報を表示します。DirectX アクティビティ セグメントに、方法についてはパケットとハードウェア キューによって処理される DMA 表示されます。マーカーに、説明についての情報およびマーカーの型が表示されます。I\/O アクセスするには、読み取りまたは書き込むファイルについての情報、およびバイト数が表示されます。  
  
## 参照  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)