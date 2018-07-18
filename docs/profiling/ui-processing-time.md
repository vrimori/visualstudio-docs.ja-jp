---
title: UI 処理時間 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad48cd912bfdc117496bc9f876a1a2174e76dc04
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34477536"
---
# <a name="ui-processing-time"></a>UI 処理時間
タイムライン内のこれらのセグメントは、UI 処理として分類されるブロック時間と関連付けられています。 これは、スレッドが Windows メッセージをポンプしているか、他のユーザー インターフェイス (UI) の作業を実行していることを意味します。 この期間中、同時実行ビジュアライザーが UI 処理としてカウントしている API で、スレッドがブロックされています。 `GetMessage()` や `MsgWaitForMultipleObjects()` などの API がこのグループになります。  
  
 定義済みのブロッキング API が識別されない場合、呼び出し履歴とプロファイル レポートを確認して、遅延の根本的な原因を判断します。  
  
 UI 処理カテゴリは、GUI アプリケーションの応答性を理解するのに役立ち、UI の応答性に依存するアプリケーションにはこのカテゴリが適しています。 たとえば、アプリケーション内の UI スレッドが UI 処理で 100% の時間を達成した場合、応答性が高いと思われます。 ただし、UI スレッドが他のカテゴリで長時間を費やしている場合は、根本的な原因を見つけて、そのスレッドでの UI 以外のカテゴリを減らすためのオプションを検討してください。  
  
## <a name="see-also"></a>関連項目  
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)