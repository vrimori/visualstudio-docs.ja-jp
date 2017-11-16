---
title: "GPU アクティビティ グラフ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 964846b5a2cc06eaf03fa695e4f1c0aeb9efdca4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-graph"></a>GPU アクティビティ グラフ
同時実行ビジュアライザーの GPU アクティビティ グラフには、一定期間使用した DirectX エンジン数によってシステム上の DirectX アクティビティのレベルが測定され、表示されます。  グラフには、具体的にどのエンジンが使用されたかは表示されません。  GPU の作業を処理しているエンジンは使用中と見なされます。  
  
## <a name="gpu-activity-graph-colors"></a>GPU アクティビティ グラフの色  
 緑は現在のプロセスによる DirectX エンジンの消費量を示しています。  
  
 淡い灰色は、システム上の他のプロセスによる DirectX エンジンの消費量を示しています。 他のプロセスによる DirectX エンジンの消費量を減らすには、システム上で実行される他のプロセスの数を削減します。  
  
 白はシステム上で利用可能な未使用の DirectX エンジンを示します。 さらに用途が見つかればプロセスで使用できるエンジンです。 一部のエンジンは、特定のタスクにしか使用できません。  
  
## <a name="see-also"></a>関連項目  
 [使用状況ビュー](../profiling/utilization-view.md)