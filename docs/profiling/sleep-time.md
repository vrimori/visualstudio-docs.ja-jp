---
title: "スリープ時間 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4385fd42c14d13e83f85683ef33a613fd6f78765
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sleep-time"></a>スリープ時間
タイムライン内のこれらのセグメントは、スリープとして分類されるブロック時間と関連付けられています。 スリープのカテゴリは、スレッドが自発的にその論理コアを明け渡して、処理を行わなかったことを示しています。 この期間中、同時実行ビジュアライザーがスリープとしてカウントしている API で、1 つのスレッドがブロックされています。 `Sleep()` や `SwitchToThread()` などの API がこのグループになります。  
  
## <a name="see-also"></a>参照  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)