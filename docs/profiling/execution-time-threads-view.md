---
title: 実行時間 (スレッド ビュー) | Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b06532771aaa432deccb8040c7dd7e5962dd15f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764431"
---
# <a name="execution-time-threads-view"></a>実行時間 (スレッド ビュー)
スレッド ビュー タイムラインのこれらのセグメントは、スレッドがシステムの論理コア上で動作中である場合、実行時間を表します。  
  
 スレッド ステータスの変更は、カーネル コンテキスト スイッチ イベントを介して検出されます。 Windows イベント トレーシング (ETW) でミリ秒ごとにサンプル履歴がキャプチャされます。 非常に短い緑のセグメントでは、サンプルが取得されない可能性があります。 そのため、一部の短い実行セグメントには、呼び出し履歴が表示されない場合があります。  
  
 実行セグメントをクリックすると、同時実行ビジュアライザーがクリックの位置に最も近いサンプル履歴を表示します。 そのサンプル履歴の場所は、タイムラインの上に黒の矢印 (キャレット) で示され、サンプル履歴が **[現在]** タブに表示されます。  
  
 現在のビューのすべての実行セグメントについて、従来のサンプリング プロファイルを参照するには、表示されているタイムライン プロファイルで **[実行]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [実行プロファイル レポート](../profiling/execution-profile-report.md)   
 [スレッド ビュー](../profiling/threads-view-parallel-performance.md)