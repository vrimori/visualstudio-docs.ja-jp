---
title: "概要ビュー - サンプリング データ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c78ba45fda91650b5b7deb37ce9fd5dabbee6fb3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="summary-view---sampling-data"></a>概要ビュー - サンプリング データ
概要ビューでは、プロファイリング実行で最もパフォーマンス負荷の高い関数についての情報を表示します。 通知リンクとレポート リストの説明など詳細については、「[Summary View](../profiling/summary-view.md) (概要ビュー)」をご覧ください。  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。 UWP アプリにも新しい収集手法が必要です。 「[Windows 8 および Windows Server 2012 アプリケーションのパフォーマンス ツール](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
## <a name="timeline-graph"></a>タイムライン グラフ  
 [概要] ビューのタイムライン グラフには、プロファイリングが行われた期間中のプロファイリング対象アプリケーションのプロセッサ (CPU) 使用率が表示されます。 タイムライン グラフを使用すると、選択した期間に対してフィルター処理した結果を表示できます。 詳細については、「[How to: Filter Report Views from the Summary Timeline](../profiling/how-to-filter-report-views-from-the-summary-timeline.md) (方法: 概要ビューのタイムラインからレポート ビューをフィルター処理する)」をご覧ください。  
  
## <a name="hot-path"></a>ホット パス  
 **[ホット パス]** には、大部分のサンプルが収集された実行パスが表示されます。 関数をクリックすると、その関数の [関数の詳細] ビューが表示されます。 関数のその他のビューを表示するには、関数を右クリックし、一覧からビューをクリックします。  
  
 **[ホット パス]** には、関数ごとに次のデータが含まれています。  
  
|Column|説明|  
|------------|-----------------|  
|**Name**|関数の名前。|  
|**包括サンプル %**|この関数またはこの関数によって呼び出された関数を実行したときに発生したすべてのサンプルの割合。|  
|**排他サンプル %**|この関数が関数本体のコードを実行していたときに発生したすべてのサンプルの割合。 この関数によって呼び出された関数で収集されたサンプルは含まれません。|  
  
## <a name="functions-doing-most-individual-work"></a>最も頻繁に個別の作業を実行している関数  
 **[最も頻繁に個別の作業を実行している関数]** リストには、プロファイリング実行で排他サンプル数が最大の関数が表示されます。 排他サンプルは、サンプルの収集時に、関数が独自のコードを実行している場合に、関数に割り当てられます。 排他サンプルは、サンプルの収集時に、関数が別の関数を呼び出している場合は、関数に割り当てられません。 排他サンプルの数が多いということは、関数自体で膨大な時間が費やされたことを示します。  
  
 関数をクリックすると、その関数の [関数の詳細] ビューが表示されます。 関数のその他のビューを表示するには、関数を右クリックし、一覧からビューをクリックします。  
  
 **[最も頻繁に個別の作業を実行している関数]** には、関数ごとに次のデータが含まれています。  
  
|Column|説明|  
|------------|-----------------|  
|**Name**|関数の名前。|  
|**サンプル % (関数のみ)**|この関数が関数本体のコードを実行していたときに収集された、プロファイリング実行内のすべてのサンプルの割合。 この関数から呼び出された関数が実行されていたときに収集されたサンプルは除外されます。|  
  
## <a name="see-also"></a>参照  
 [概要ビュー](../profiling/summary-view-dotnet-memory-data.md)   
 [概要ビュー](../profiling/summary-view-instrumentation-data.md)