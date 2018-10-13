---
title: GPU アクティビティ (ページング) | Microsoft Docs
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
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 015fa34d2bb87cf98a64fb3431a6440202cf729b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195859"
---
# <a name="gpu-activity-paging"></a>GPU アクティビティ (ページング)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[スレッド] タブの **[GPU アクティビティ (ページング)]** セグメントは、GPU がページング要求の処理に要した時間を示します。  セグメントの長さは、GPU がダイレクト メモリ アクセス (DMA) ページング パケットを処理していた時間を表します。 通常、ページング パケットは CPU と GPU の間のメモリの転送に関連付けられています。  
  
 GPU ページング セグメントを選択した場合、**[現在]** タブのレポートには処理された DMA パケットの情報が表示されます。 これには、パケットが DirectX に関連するハードウェア キューで待機していた時間、DMA パケットを送信したプロセス、パケットの処理に要した時間が含まれます。  
  
## <a name="see-also"></a>関連項目  
 [使用状況ビュー](../profiling/utilization-view.md)



