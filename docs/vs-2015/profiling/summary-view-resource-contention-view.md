---
title: 概要ビュー - リソース競合ビュー | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf83509cd56343001a94da619b9246464ed75bdf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533535"
---
# <a name="summary-view---resource-contention-view"></a>概要ビュー - リソース競合ビュー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[概要ビュー - リソース競合ビュー](https://docs.microsoft.com/visualstudio/profiling/summary-view-resource-contention-view)します。  
  
概要ビューでは、リソースへのアクセス待機中に中断されたスレッドまたはプロセスが含まれるアプリケーションのイベントに関する情報を表示します。  
  
 通知リンクとレポート リストの説明など詳細については、「[Summary View](../profiling/summary-view.md) (概要ビュー)」をご覧ください。  
  
## <a name="timeline-graph"></a>タイムライン グラフ  
 概要ビューのタイムライン グラフには、プロファイリングが行われた期間の、プロファイリングされたアプリケーションの競合イベントの数が表示されます。 タイムライン グラフを使用すると、選択した期間に対してフィルター処理した結果を表示できます。 詳細については、「[How to: Filter Report Views from the Summary Timeline](../profiling/how-to-filter-report-views-from-the-summary-timeline.md) (方法: 概要ビューのタイムラインからレポート ビューをフィルター処理する)」をご覧ください。  
  
## <a name="most-contended-resources"></a>最も競合の多いリソース  
 **[最も競合の多いリソース]** では、最も多くの競合イベントが発生したアプリケーションのリソースが一覧表示されます。 リソース名をクリックすると競合ビューが表示されます。 競合ビューには、スレッドごとのリソースの競合の詳細なタイムラインが表示されます。  
  
 **[最も競合の多いリソース]** には、各リソースの次のデータが含まれます。  
  
|Column|説明|  
|------------|-----------------|  
|**Name**|リソースの名前。|  
|**競合 %**|プロファイル データのすべての競合イベントに対する、このリソースに関する競合イベントの割合。|  
  
## <a name="most-contended-thread"></a>最も競合の多いスレッド  
 **[最も競合の多いスレッド]** では、最も多くの競合イベントが発生したアプリケーションのスレッドが一覧表示されます。 スレッド名をクリックすると競合ビューが表示され、スレッドごとのリソースの競合の詳細なタイムラインが表示されます。  
  
 **最も競合の多いスレッド** には、各スレッドの次のデータが含まれます。  
  
|Column|説明|  
|------------|-----------------|  
|**ID**|スレッド ID です|  
|**Name**|スレッドを所有するプロセスの名前。|  
|**競合 %**|プロファイル データのすべての競合イベントに対する、このリソースに関する競合イベントの割合。|



