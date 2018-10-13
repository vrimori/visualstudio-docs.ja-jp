---
title: アクティビティ ビュー (レガシ) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: e5fb8368228118b210865b1a351d12b1b5da4b27
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229315"
---
# <a name="activity-views-legacy"></a>アクティビティ ビュー (レガシ)
[!INCLUDE[wf](../includes/wf-md.md)] が提供するアクティビティの多くには、従来の [!INCLUDE[wfd1](../includes/wfd1-md.md)]で使用できるデザイン ビューが複数あります。ワークフローは、これらのアクティビティを使用して作成されます。 アクティビティ デザイナーをドラッグすると、**ツールボックス**には、デザイン画面で、その後いずれかを使用してさまざまなデザイン ビューを切り替えることができます、アクティビティを選択するたびに、**ワークフロー**メニューか、選択したアクティビティを右クリックします。 さらに、選択したアクティビティの名前の上にポインタを移動すると、ドロップダウン タブのセットが表示され、これを使ってさまざまなビューに切り替えることができます。  
  
 すべてのアクティビティに少なくとも 1 つのビューこれは、既定のビューからのアクティビティ デザイナーをドラッグすると表示される、**ツールボックス**デザイン サーフェイスにします。 このアクティビティの既定のビューは、 **[アクティビティの種類] を表示**オプション メニューおよびタブで、たとえば、**ビューの並列**します。 ほとんどのアクティビティには他にもビューがあり、ビューの種類はアクティビティによってさまざまに異なります。 など、 [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)アクティビティは補正ビューと[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)アクティビティにイベントを表示します。 Windows Workflow Foundation に付属しているアクティビティの多くが**キャンセル ハンドラーの**と**エラーの表示**ビューにビューをデザイン、 [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)および[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)それらに関連付けられています。  
  
 各ビューの名前と説明の一覧を次の表に示します。  
  
|メニュー/タブ オプション|説明|  
|----------------------|-----------------|  
|**[アクティビティの種類] ビュー**|このメニュー オプションまたはタブ オプションをクリックすると、選択したアクティビティの既定のビューがグラフィック表示されます。|  
|**キャンセル ハンドラーの表示**|このメニュー オプションまたはタブ オプションが表示、 [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)選択したアクティビティに関連付けられています。|  
|**エラー ハンドラー**|このメニュー オプションまたはタブ オプションが表示、 [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)選択したアクティビティに関連付けられています。|  
|**補正ハンドラの表示**|このメニュー オプションまたはタブ オプションが表示、 [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)選択した[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)します。|  
|**イベント ハンドラーの表示**|このメニュー オプションまたはタブ オプションが表示、 [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)選択した、 [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)します。|  
  
 同様のビューについては、次を参照してください。[シーケンシャル ワークフロー ビュー (レガシ)](../workflow-designer/sequential-workflow-views-legacy.md)します。  
  
## <a name="see-also"></a>関連項目  
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)   
 [シーケンシャル ワークフロー ビュー (レガシ)](../workflow-designer/sequential-workflow-views-legacy.md)