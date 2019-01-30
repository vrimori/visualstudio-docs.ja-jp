---
title: GPU アクティビティ (他のプロセス) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c7d68547e0c2d0b056e2c60f1e9e183270841c6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030263"
---
# <a name="gpu-activity-other-processes"></a>GPU アクティビティ (他のプロセス)
コンカレンシー ビジュアライザーのスレッド ビューの **[GPU アクティビティ (他のプロセス)]** セグメントは、GPU がシステム上の他のプロセスのために要求を処理していた時間を示します。 これらの要求はダイレクト メモリ アクセス (DMA) パケットとして GPU に送信されます。  セグメントの長さは GPU でパケットが処理されていた時間を表します。  
  
 このようなセグメントを選択した場合、**[現在]** タブのレポートには処理されたパケットの情報が表示されます。  情報には、パケットが DirectX に関連するハードウェア キューで待機していた時間、パケットを送信したプロセス、パケットの処理に要した時間が含まれます。