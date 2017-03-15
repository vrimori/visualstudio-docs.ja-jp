---
title: "コア ビュー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.cores"
helpviewer_keywords: 
  - "同時実行ビジュアライザー、コア ビュー"
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# コア ビュー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コア ビューは、スレッドの実行が論理プロセッサ コアにどのようにマップされるかを示します。  サーバー アプリケーションを作成する場合は、このビューには、スレッドの関係またはスレッド プール管理を使用してキャッシュ パフォーマンスを最適化できます。  また、スレッド アフィニティの使用は、コア間の移行に関する問題を低下させる可能性があるケースを調べることができます。  コア ビューに 2 部分 \(グラフと凡例があります。  
  
 グラフの x 軸の y 軸と時間の論理コアが表示されます。  コア間の移動を時間の経過に沿って追跡できるように、グラフ内のすべてのスレッドに固有の色になります。  凡例の領域で選択してこのグラフのスレッドをフィルター処理できます。  
  
 凡例の領域にグラフの各色のエントリがあります。  各エントリは、クロスコアのコンテキスト スイッチのスレッドの色と名前、数値、コンテキスト スイッチの合計数、およびコア間にまたがるコンテキスト スイッチの割合を示します。  凡例は、クロスコアのコンテキスト スイッチの数が多いものから順に並べ替えられます。  これは、表示されている時間範囲で実行したスレッドだけが一覧表示されます。リストは縮小またはパンする更新されます。  
  
## 参照  
 [同時実行ビジュアライザー](../profiling/concurrency-visualizer.md)   
 [使用状況ビュー](../profiling/utilization-view.md)   
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)