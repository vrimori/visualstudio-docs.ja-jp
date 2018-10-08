---
title: 同期時間 | Microsoft Docs
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
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b1ca6b7a0d6e7f7c3be41bb091674a3526edf53
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548384"
---
# <a name="synchronization-time"></a>同期時間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[同期時間](https://docs.microsoft.com/visualstudio/profiling/synchronization-time)します。  
  
タイムライン内のこれらのセグメントは、同期として分類されたブロック時間に関連付けられています。 同期でスレッドにブロックされたマークが付いている場合、次のいずれかを示しています。  
  
-   スレッドの実行が、`EnterCriticalSection()` または `WaitForSingleObject()` などの既知のスレッド同期 API を呼び出す結果になった可能性がある。  
  
-   API 照合アルゴリズムが全体として包括的にならず、そのために他のカテゴリにマップされている可能性がある一部の API も同期として表示されている可能性がある。呼び出し履歴内のフレームの最終的な到達先が、このカテゴリにマップされた、基になるカーネルをブロックしている基本要素である場合にこの状態になります。  
  
 スレッド ブロック イベントの根本的な原因を理解するために、ブロック呼び出し履歴とプロファイル レポートをよく調べてください。  
  
## <a name="see-also"></a>関連項目  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)



