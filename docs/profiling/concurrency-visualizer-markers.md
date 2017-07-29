---
title: "同時実行ビジュアライザー マーカー | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
caps.latest.revision: 12
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 29aa9de1c8fcba0c51a05751666d2931aa68aaa4
ms.contentlocale: ja-jp
ms.lasthandoff: 05/30/2017

---
# <a name="concurrency-visualizer-markers"></a>同時実行ビジュアライザー マーカー
同時実行ビジュアライザーのマーカーはアプリ内のイベントを表すアイコンです。  通常、アプリはこれらのイベントを生成して、アプリケーションでのフェーズまたは出現回数を指定します。  アプリ、またはアプリで使用するライブラリとランタイムでイベントを生成することができます。  
  
## <a name="kinds-of-markers"></a>マーカーの種類  
 同時実行ビジュアライザーでは、アプリケーション イベントを表す 3 種類のマーカー (フラグ、メッセージ、スパン) が使用されます。  
  
1.  アプリの特定の時点を示す場合は、*フラグ*を使用します。  たとえば、変数値が特定のしきい値に達したことや、例外がスローされたことを表す場合はフラグを使用できます。  
  
2.  *メッセージ*も一定の時点をマークしますが、ログ スタイルのトレースで使用できます。  たとえば、ログ ファイルにダンプされている場合、メッセージ呼び出しでラップできるため、同時実行ビジュアライザーでトレースおよび表示することができます。 また、同時実行ビジュアライザーを使用して、このデータを CSV ファイルにエクスポートすることもできます。  
  
3.  *スパン*は、いずれかのフェーズなど、アプリにおける時間間隔を表します。  
  
## <a name="marker-linkage-to-threads"></a>スレッドへのマーカー リンケージ  
 マーカーを生成するスレッドにはそれぞれ別のタイムライン チャネルがあります。  マーカー イベントを生成するスレッドの ID は、マーカー チャネルの説明の横に表示されます。  マーカー チャネルの左側に表示される ID は、現在のプロセス内の別のスレッドの ID と一致します。  
  
## <a name="marker-importance"></a>マーカーの重要度  
 マーカーでは、4 つの重要度レベル (低、通常、高、重大) のいずれかを設定できます。  重要度レベルに基づいて、マーカーのソースをフィルター処理することができます。  たとえば、重要度が通常または重大である特定のソースのみのマーカーを表示する場合、[[詳細設定]](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ダイアログ ボックスでフィルターを構成することができます。マーカーの重要度はそのヒント、および [[マーカー レポート]](../profiling/markers-report.md) に表示されます。  
  
## <a name="marker-category"></a>マーカーのカテゴリ  
 マーカーのカテゴリは、同じソースからのマーカー イベントのグループを示します。  同時実行ビジュアライザーでは色を使用して、さまざまなカテゴリのフラグとスパンを区別します。 特定のイベント プロバイダーからのマーカー イベントをフィルター処理するために、カテゴリを使用するように同時実行ビジュアライザーを構成することができます。  フィルターを構成するには、[[詳細設定]](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ダイアログ ボックスを使用します。  
  
## <a name="known-sources-of-markers"></a>マーカーの既知のソース  
 ETW プロバイダーは、特定の制約に準拠している限り、マーカーを生成できます。 マーカーの追加のイベント ソースをリッスンするように同時実行ビジュアライザーを構成することができます。 既定では、以下のイベント ソースをリッスンします。  
  
-   [同時実行ビジュアライザー SDK](../profiling/concurrency-visualizer-sdk.md)  
  
-   [タスク並列ライブラリ (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)  
  
-   [データフロー](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)  
  
-   [Parallel LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)  
  
-   [同時実行ランタイム](/cpp/parallel/concrt/concurrency-runtime)  
  
-   [シナリオ マーカーのサポート](http://msdn.microsoft.com/en-us/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
-   [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)  
  
 [[詳細設定]](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) ダイアログ ボックスの [マーカー] タブを使用して、同時実行ビジュアライザーでさまざまなソースからのマーカーを表示するかどうかを制御できます。また、重要度とカテゴリに基づいて、マーカーをフィルター処理することができます。  
  
## <a name="markers-from-eventsource"></a>EventSource からのマーカー  
 同時実行ビジュアライザーでは、EventSource イベントも表示できます。  詳細については、「[マーカーとしての EventSource イベントの視覚化](../profiling/visualizing-eventsource-events-as-markers.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [フラグ マーカー](../profiling/flag-markers.md)   
 [メッセージ マーカー](../profiling/message-markers.md)   
 [スパン マーカー](../profiling/span-markers.md)   
 [マーカーとしての EventSource イベントの視覚化](../profiling/visualizing-eventsource-events-as-markers.md)
