---
title: "使用状況ナビゲーター | Microsoft Docs"
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
  - "vs.cv.performance.utilizationnavigator"
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用状況ナビゲーター
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

同時実行ビジュアライザーでは、トレースの時間間隔の選択に使用率ナビゲーターを使用できます。  同時実行ビジュアライザーは、ターゲット プロセスによる CPU コアの使用状況を時間の経過とともに表示されます。  これで、CPU 使用率のパターンを調査しやすく、他のビューの使用率データとデータの比較を実行できます。  使用率ナビゲーターは同時実行ビジュアライザーのすべてのビューの上部に表示されます。  次の図は、CPU 使用量ナビゲーターを示します。  
  
 ![選択されたタイムフレームを示す使用状況ナビゲーター](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator")  
使用率ナビゲーター、指定したタイム フレーム  
  
 図では、指定した間隔は、Thumb と呼ばれる赤い四角形によって定義されます。  
  
 ここに表示されている時間範囲を処理するために使用率ナビゲーターを使用することで、T:  
  
-   Thumb の左右をドラッグして移動できます。\(キーボード: フォーカスを Thumb に移動し、左右の方向キーを押します\)。  
  
-   ハンドルの 1 つをドラッグして間隔の範囲を変更できます。\(キーボード: フォーカスをハンドルに移動し、右側または左方向キーを押します\)。  
  
 異なる同時実行ビジュアライザーのズーム コントロールを使用して、間隔を変更した場合、その変更を反映して使用率ナビゲーターの更新。