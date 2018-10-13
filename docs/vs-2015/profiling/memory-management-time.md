---
title: メモリ管理時間 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 391f231a604af3fe0c47242acf7ea49c67f40f34
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181325"
---
# <a name="memory-management-time"></a>メモリ管理時間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

タイムライン内のこれらのセグメントは、メモリ管理として分類されたブロック時間に関連付けられます。 これは、ページングなど、メモリ管理操作に関連付けられているイベントによって、スレッドがブロックされていることを意味します。 この期間中、コンカレンシー ビジュアライザーがメモリ管理としてカウントする API またはカーネルの状態で、スレッドがブロックされています。 これには、ページングやメモリの割り当てなどのイベントが含まれます。  
  
 メモリ管理として分類されたブロックの基になる理由をよく理解するために、関連のコール スタックとプロファイル レポートを確認してください。  
  
## <a name="see-also"></a>関連項目  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)



