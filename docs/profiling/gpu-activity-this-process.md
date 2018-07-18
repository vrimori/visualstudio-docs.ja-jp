---
title: GPU アクティビティ (このプロセス) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7fe5512cf131dfede701fb47df2ef956c01437d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31570386"
---
# <a name="gpu-activity-this-process"></a>GPU アクティビティ (このプロセス)
同時実行ビジュアライザーのスレッド ビューの **[GPU アクティビティ (このプロセス)]** セグメントは、GPU が現在のプロセスに代わり、要求を処理していた時間を示します。 これらの要求はダイレクト メモリ アクセス (DMA) パケットとして GPU に送信されます。 セグメントの長さは、GPU が現在のプロセスに代わって DMA パケットを処理していた時間を表します。  
  
 GPU アクティビティ セグメントを選択した場合、**[現在]** タブには処理された DMA パケットの情報が表示されます。 情報には、パケットが DirectX に関連するハードウェア キューで待機していた時間、パケットを送信したプロセス、およびパケットの処理に要した時間が含まれます。 現在のプロセス以外のプロセスによって、DMA パケットが GPU に物理的に送信されることがあります。 現在のプロセスに代わって他のプロセスが GPU に作業を送信すると、同時実行ビジュアライザーによって検出されます。