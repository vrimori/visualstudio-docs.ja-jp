---
title: "GPU アクティビティ グラフ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cpu.graph.gpu"
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# GPU アクティビティ グラフ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

同時実行ビジュアライザーで GPU アクティビティ グラフは時間の経過とともに使用されている DirectX エンジンの個数されるシステムの DirectX アクティビティのレベルを表示します。グラフには、任意のエンジンが使用されているかを示します。エンジンは、GPU 作業を処理して使用中であると見なされます。  
  
## GPU アクティビティ グラフの色  
 緑色は、現在のプロセスによって DirectX エンジンの使用を示します。  
  
 明るい灰色は、システム上の他のプロセスによって DirectX エンジンの使用を示します。  他のプロセスによって DirectX エンジンの使用を単純化するには、システム上の他の実行中のプロセスの数を単純化する。  
  
 白はシステムの DirectX 未使用のエンジンが使用できるかどうかを示します。  これらのエンジンはそれらを開発するための手段を見つけることができる場合は、プロセスで使用できます。  あるエンジンは、特定の種類のタスクにのみ使用できます。  
  
## 参照  
 [使用状況ビュー](../profiling/utilization-view.md)