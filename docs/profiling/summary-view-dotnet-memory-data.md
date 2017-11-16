---
title: "概要ビュー - .NET メモリ データ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 968d46c4fe771229647282c719815982d81bf416
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="summary-view---net-memory-data"></a>概要ビュー - .NET メモリ データ
概要ビューには、最も多くのメモリを割り当てた .NET 関数と型、およびプロファイリング実行で作成回数が最も多い型に関する情報が一覧表示されます。 通知リンクやレポートの一覧の説明など、詳細については、「[概要ビュー](../profiling/summary-view.md)」をご覧ください。  
  
## <a name="timeline-graph"></a>タイムライン グラフ  
 概要ビューのタイムライン グラフには、プロファイリングが行われた期間のプロファイリングされたアプリケーション別にプロセッサ (CPU) 使用率が表示されます。 タイムライン グラフを使用すると、選択した期間に対してフィルター処理した結果を表示できます。 詳細については、「[方法: 概要ビューのタイムラインからレポート ビューをフィルター処理する](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)」をご覧ください。  
  
## <a name="functions-allocating-most-memory"></a>最も多くのメモリを割り当てている関数  
 プロファイリング実行で最も多くのメモリのバイト数を割り当てた関数が一覧表示されます。  
  
|Column|説明|  
|------------|-----------------|  
|**名前**|関数の名前。|  
|**バイト %**|プロファイリング実行で割り当てられたすべてのバイト数に対する、この関数、またはこの関数によって呼び出された子関数によって割り当てられたバイト数の割合。|  
  
## <a name="types-with-most-memory-allocated"></a>最も多くのメモリを割り当てられた型  
 プロファイリング実行で最も多くのメモリのバイト数が割り当てられた型が一覧表示されます。  
  
|Column|説明|  
|------------|-----------------|  
|**名前**|型の名前。|  
|**バイト %**|プロファイリング実行で割り当てられたすべてのバイト数に対する、この型に対して割り当てられたバイト数の割合。|  
  
## <a name="types-with-most-instances"></a>最も多くのインスタンスを伴う型  
 プロファイリング実行で作成回数が最も多い型が一覧表示されます。 以下をご覧ください。  
  
|Column|説明|  
|------------|-----------------|  
|**名前**|型の名前。|  
|**インスタンス %**|プロファイリング実行で作成された .NET オブジェクトの合計数に対する、この型のインスタンスであったオブジェクトの割合。|  
  
## <a name="see-also"></a>関連項目  
 [概要ビュー](../profiling/summary-view-sampling-data.md)   
 [概要ビュー](../profiling/summary-view-instrumentation-data.md)