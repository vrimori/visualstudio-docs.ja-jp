---
title: コア ビュー | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bce1c1ca458b8d06af89c669a76a2a93371fad5a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537187"
---
# <a name="cores-view"></a>コア ビュー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[コア ビュー](https://docs.microsoft.com/visualstudio/profiling/cores-view)します。  
  
コア ビューは、スレッドの実行が論理プロセッサ コアにどのようなマップされたかを示しています。 サーバー アプリケーションを開発している場合、このビューは、スレッド アフィニティまたはスレッド プール管理を使ってキャッシュのパフォーマンスを最適化するのに役立ちます。 また、スレッド アフィニティを使うことでコア間の移行の問題が悪化した可能性がある場合の調査にも役立ちます。 コア ビューには、グラフと凡例の 2 つの部分があります。  
  
 グラフでは、Y 軸に論理コア、X 軸に時間が表示されます。 グラフではすべてのスレッドに固有の色が使われていて、時間経過を追ってコア間のスレッドの移動を追跡できます。 凡例領域でスレッドを選ぶことにより、このグラフ上のスレッドをフィルター処理できます。  
  
 凡例領域には、グラフの各色に対するエントリがあります。 各エントリには、スレッドの色と名前、クロスコア コンテキスト スイッチの数、コンテキスト スイッチの総数、およびクロスコア コンテキスト スイッチの割合が示されます。 凡例は、クロスコア コンテキスト スイッチの数が多い順に並べられています。 表示されている時間範囲中に実行されたスレッドのみが一覧表示されます。  ズームまたはパンすると、リストが更新されます。  
  
## <a name="see-also"></a>関連項目  
 [コンカレンシー ビジュアライザー](../profiling/concurrency-visualizer.md)   
 [使用状況ビュー](../profiling/utilization-view.md)   
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)



