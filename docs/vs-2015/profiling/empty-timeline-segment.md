---
title: 空のタイムライン セグメント | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4ac39a776cb7e6c2c9cbce648c0b3ca3ebc86783
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770746"
---
# <a name="empty-timeline-segment"></a>空のタイムライン セグメントです
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

コンカレンシー ビジュアライザーでは、タイムラインのセクションが空になる (白の背景を持つ) の理由は、チャネルの種類によって異なります。  
  
-   CPU スレッド チャネルの場合は、タイムラインのこの部分の間にスレッドが存在しなかったことを意味します。 スレッドについて知りたい場合は、ズーム コントロールまたは水平スクロールを使って、実行セクションを見つけることができます。  
  
-   I/O チャネルの場合は、その時点でターゲット プロセスに対するディスク アクセスが発生しなかったこと意味します。  
  
-   DirectX チャネルの場合は、タイムラインのこの部分の間にターゲット プロセスに対する GPU 処理が実行されなかったことを意味します。  
  
-   マーカー チャネルの場合は、マーカーが生成されなかったことを意味します。  
  
## <a name="see-also"></a>「  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)   
 [ズーム コントロール (スレッド ビュー)](../profiling/zoom-control-threads-view.md)
