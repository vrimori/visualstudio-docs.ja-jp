---
title: コア ビュー | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f9fdd88640999759fe729b3949785a79e763986
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35669506"
---
# <a name="cores-view"></a>コア ビュー
**コア ビュー** には、スレッド実行が論理プロセッサのコアにどのようにマッピングされたかを示します (**[分析]** > **[同時実行ビジュアライザー]** を選択して、同時実行ビジュアライザーを開始します)。 サーバー アプリケーションを開発している場合、このビューは、スレッド アフィニティまたはスレッド プール管理を使ってキャッシュのパフォーマンスを最適化するのに役立ちます。 また、スレッド アフィニティを使うことでコア間の移行の問題が悪化した可能性がある場合の調査にも役立ちます。 コア ビューには、グラフと凡例の 2 つの部分があります。  
  
 グラフでは、Y 軸に論理コア、X 軸に時間が表示されます。 グラフではすべてのスレッドに固有の色が使われていて、時間経過を追ってコア間のスレッドの移動を追跡できます。 凡例領域でスレッドを選ぶことにより、このグラフ上のスレッドをフィルター処理できます。  
  
 凡例領域には、グラフの各色に対するエントリがあります。 各エントリには、スレッドの色と名前、クロスコア コンテキスト スイッチの数、コンテキスト スイッチの総数、およびクロスコア コンテキスト スイッチの割合が示されます。 凡例は、クロスコア コンテキスト スイッチの数が多い順に並べられています。 表示されている時間範囲中に実行されたスレッドのみが一覧表示されます。  ズームまたはパンすると、リストが更新されます。  
  
## <a name="see-also"></a>関連項目  
 [同時実行ビジュアライザー](../profiling/concurrency-visualizer.md)   
 [使用状況ビュー](../profiling/utilization-view.md)   
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)