---
title: "GPU アクティビティ (ページング) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 10a4f9a0c83e18da6fb9f45a2ac4fded913d2723
ms.lasthandoff: 02/22/2017

---
# <a name="gpu-activity-paging"></a>GPU アクティビティ (ページング)
[スレッド] タブの **[GPU アクティビティ (ページング)]** セグメントは、GPU がページング要求の処理に要した時間を示します。  セグメントの長さは、GPU がダイレクト メモリ アクセス (DMA) ページング パケットを処理していた時間を表します。 通常、ページング パケットは CPU と GPU の間のメモリの転送に関連付けられています。  
  
 GPU ページング セグメントを選択した場合、**[現在]** タブのレポートには処理された DMA パケットの情報が表示されます。 これには、パケットが DirectX に関連するハードウェア キューで待機していた時間、DMA パケットを送信したプロセス、パケットの処理に要した時間が含まれます。  
  
## <a name="see-also"></a>関連項目  
 [使用状況ビュー](../profiling/utilization-view.md)
