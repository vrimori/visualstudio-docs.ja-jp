---
title: "GPU アクティビティ (このプロセス) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 255a1ff62d4f9c444169e1330dcd11eb8e1030ed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-this-process"></a>GPU アクティビティ (このプロセス)
同時実行ビジュアライザーのスレッド ビューの **[GPU アクティビティ (このプロセス)]** セグメントは、GPU が現在のプロセスに代わり、要求を処理していた時間を示します。 これらの要求はダイレクト メモリ アクセス (DMA) パケットとして GPU に送信されます。 セグメントの長さは、GPU が現在のプロセスに代わって DMA パケットを処理していた時間を表します。  
  
 GPU アクティビティ セグメントを選択した場合、**[現在]** タブには処理された DMA パケットの情報が表示されます。 情報には、パケットが DirectX に関連するハードウェア キューで待機していた時間、パケットを送信したプロセス、およびパケットの処理に要した時間が含まれます。 現在のプロセス以外のプロセスによって、DMA パケットが GPU に物理的に送信されることがあります。 現在のプロセスに代わって他のプロセスが GPU に作業を送信すると、同時実行ビジュアライザーによって検出されます。