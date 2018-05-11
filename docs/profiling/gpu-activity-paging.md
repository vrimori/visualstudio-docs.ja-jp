---
title: GPU アクティビティ (ページング) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 822b65309d1db2423b3c5798c51db6c9631bf835
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="gpu-activity-paging"></a>GPU アクティビティ (ページング)
[スレッド] タブの **[GPU アクティビティ (ページング)]** セグメントは、GPU がページング要求の処理に要した時間を示します。  セグメントの長さは、GPU がダイレクト メモリ アクセス (DMA) ページング パケットを処理していた時間を表します。 通常、ページング パケットは CPU と GPU の間のメモリの転送に関連付けられています。  
  
 GPU ページング セグメントを選択した場合、**[現在]** タブのレポートには処理された DMA パケットの情報が表示されます。 これには、パケットが DirectX に関連するハードウェア キューで待機していた時間、DMA パケットを送信したプロセス、パケットの処理に要した時間が含まれます。  
  
## <a name="see-also"></a>参照  
 [使用状況ビュー](../profiling/utilization-view.md)