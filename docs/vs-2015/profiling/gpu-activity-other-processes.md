---
title: GPU アクティビティ (他のプロセス) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a3b0e97d82d67916aa71f932038930dba48c17e4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787520"
---
# <a name="gpu-activity-other-processes"></a>GPU アクティビティ (他のプロセス)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

コンカレンシー ビジュアライザーのスレッド ビューの **[GPU アクティビティ (他のプロセス)]** セグメントは、GPU がシステム上の他のプロセスのために要求を処理していた時間を示します。 これらの要求はダイレクト メモリ アクセス (DMA) パケットとして GPU に送信されます。  セグメントの長さは GPU でパケットが処理されていた時間を表します。  
  
 このようなセグメントを選択した場合、**[現在]** タブのレポートには処理されたパケットの情報が表示されます。  情報には、パケットが DirectX に関連するハードウェア キューで待機していた時間、パケットを送信したプロセス、パケットの処理に要した時間が含まれます。
