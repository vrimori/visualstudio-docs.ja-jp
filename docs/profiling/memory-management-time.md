---
title: メモリ管理時間 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0284d312a4157c41f93fec17d601406c669a83c1
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238252"
---
# <a name="memory-management-time"></a>メモリ管理時間
タイムライン内のこれらのセグメントは、メモリ管理として分類されたブロック時間に関連付けられます。 このシナリオは、ページングなど、メモリ管理操作に関連付けられているイベントによって、スレッドがブロックされていることを意味します。 この期間中、同時実行ビジュアライザーがメモリ管理としてカウントする API またはカーネルの状態で、スレッドがブロックされています。 これには、ページングやメモリの割り当てなどのイベントが含まれます。  
  
 メモリ管理として分類されたブロックの基になる理由をよく理解するために、関連のコール スタックとプロファイル レポートを確認してください。  
  
## <a name="see-also"></a>関連項目  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)