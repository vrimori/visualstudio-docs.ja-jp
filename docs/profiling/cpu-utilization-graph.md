---
title: "CPU 使用状況グラフ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cpu.graph"
helpviewer_keywords: 
  - "CPU 使用状況グラフ (同時実行ビジュアライザー)、CPU 使用状況グラフ"
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# CPU 使用状況グラフ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

CPU 使用状況グラフは、アプリケーションで使用率のレベルが時間の経過とともに表示されます。  X 軸はトレースの時間を表し、Y 軸はシステムの論理コアの数を表します。  グラフには、任意の時点にどのコアがアクティブであるかは表示されません。  たとえば、2 個のコアが特定の長さの容量 50 に各実行されている場合、このビューは使用されている一つの論理コア 1。  
  
## CPU 使用状況グラフの色  
  
-   緑色は、現在のプロセスによってシステムの論理コアの使用量を示します。  
  
-   明るい灰色は、システム上の他のプロセスによる論理コアの使用量を示します。  CPU グラフの明るい灰色の高い割合は、システムが他のプロセスによって頻繁に読み込まれること、およびプロセスが高く、によって占有することを示します。  他のプロセスによる論理コアの使用量を減らすには、システム上で実行されている他のプロセスの数を減らします。  
  
-   濃い灰色は、システム プロセスによる論理コアの使用量を示します。  これを直接制御できませんが、プロセスの論理コアの使用可能状況に影響する可能性があるため、発生しているかを確認できると便利です。  
  
-   白はシステムの未使用の論理コアの使用可能状況を示します。  並列化の機会を増やすことができれば、プロセスに使用できる論理コアが増えます。  
  
## 参照  
 [使用状況ビュー](../profiling/utilization-view.md)   
 [平均 CPU 使用状況](../profiling/average-cpu-utilization.md)