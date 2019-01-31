---
title: GPU アクティビティ グラフ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4546c3be480349f3e2cb36f483fa8711bc2ac49
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769046"
---
# <a name="gpu-activity-graph"></a>GPU アクティビティ グラフ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

コンカレンシー ビジュアライザーの GPU アクティビティ グラフには、一定期間使用した DirectX エンジン数によってシステム上の DirectX アクティビティのレベルが測定され、表示されます。  グラフには、具体的にどのエンジンが使用されたかは表示されません。  GPU の作業を処理しているエンジンは使用中と見なされます。  
  
## <a name="gpu-activity-graph-colors"></a>GPU アクティビティ グラフの色  
 緑は現在のプロセスによる DirectX エンジンの消費量を示しています。  
  
 淡い灰色は、システム上の他のプロセスによる DirectX エンジンの消費量を示しています。 他のプロセスによる DirectX エンジンの消費量を減らすには、システム上で実行される他のプロセスの数を削減します。  
  
 白はシステム上で利用可能な未使用の DirectX エンジンを示します。 さらに用途が見つかればプロセスで使用できるエンジンです。 一部のエンジンは、特定のタスクにしか使用できません。  
  
## <a name="see-also"></a>「  
 [使用状況ビュー](../profiling/utilization-view.md)
