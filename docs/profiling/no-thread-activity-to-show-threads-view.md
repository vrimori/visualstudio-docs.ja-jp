---
title: "表示するスレッド アクティビティがありません (スレッド ビュー) | Microsoft Docs"
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
  - "vs.cv.threads.nothreadreport"
helpviewer_keywords: 
  - "同時実行ビジュアライザー, 表示するスレッド アクティビティがありません (スレッド ビュー)"
ms.assetid: aa5ae9d0-561d-4ef8-b36b-258ce553d50a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 表示するスレッド アクティビティがありません (スレッド ビュー)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この領域には、現在表示されている時間範囲で非表示になっていないスレッドに関するデータが表示されます。  
  
 表示される情報がない場合、次の設定を確認してください。  
  
-   ズーム レベルが高いかどうか。  範囲内にスレッド アクティビティが表示されるように、表示を縮小するかスクロールしてください。  
  
-   非表示のスレッドが多すぎないか。  その場合、すべてのスレッドを表示してください。  
  
-   **\[マイ コードのみ\]** がオンになっているかどうか。その場合、自分のコードに関するデータのみを表示できます。  システム スレッド アクティビティがあるかどうかの確認の設定をオフにしてください。  
  
-   ノイズ リダクションが低いしきい値に設定されていることを確認してください。  
  
## 参照  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)