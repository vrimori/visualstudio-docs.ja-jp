---
title: "アクティビティ ビュー (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "アクティビティ, アクティビティ ビュー"
  - "アクティビティ ビュー"
  - "ビュー, アクティビティ"
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# アクティビティ ビュー (レガシ)
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] が提供するアクティビティの多くには、従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]で使用できるデザイン ビューが複数あります。ワークフローは、これらのアクティビティを使用して作成されます。アクティビティ デザイナーを **\[ツールボックス\]** からデザイン サーフェイスにドラッグした後、そのアクティビティを選択した状態で **\[ワークフロー\]** メニューを使って、または選択したアクティビティを右クリックして、さまざまなデザイン ビューに切り替えることができます。さらに、選択したアクティビティの名前の上にポインタを移動すると、ドロップダウン タブのセットが表示され、これを使ってさまざまなビューに切り替えることができます。  
  
 各アクティビティには少なくとも 1 つのビューがあります。これは、アクティビティ デザイナーを **\[ツールボックス\]** からデザイン サーフェイスにドラッグしたときに表示される既定のビューです。この既定のアクティビティ ビューは、メニューおよびタブで **\[\[アクティビティ タイプ\] の表示\]** オプションとして表示されます \(たとえば **\[並列の表示\]**\)。ほとんどのアクティビティには他にもビューがあり、ビューの種類はアクティビティによってさまざまに異なります。たとえば、[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) アクティビティには補正ビューがあり、[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) アクティビティにはイベント ビューがあります。Windows Workflow Foundation に付属のほとんどのアクティビティには **\[キャンセル ハンドラの表示\]** および **\[エラーの表示\]** デザイン ビューがあり、それぞれに関連した [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) と [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) が表示されます。  
  
 各ビューの名前と説明の一覧を次の表に示します。  
  
|メニュー\/タブ オプション|説明|  
|--------------------|--------|  
|**\[アクティビティ タイプ\] の表示**|このメニュー オプションまたはタブ オプションをクリックすると、選択したアクティビティの既定のビューがグラフィック表示されます。|  
|**キャンセル ハンドラの表示**|このメニュー オプションまたはタブ オプションをクリックすると、選択したアクティビティに関連した [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) が表示されます。|  
|**エラー ハンドラの表示**|このメニュー オプションまたはタブ オプションをクリックすると、選択したアクティビティに関連した [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) が表示されます。|  
|**補正ハンドラの表示**|このメニュー オプションまたはタブ オプションをクリックすると、選択した [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) に関連した [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) が表示されます。|  
|**イベント ハンドラの表示**|このメニュー オプションまたはタブ オプションをクリックすると、選択した [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) に関連した [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) が表示されます。|  
  
 同様のビューについては、「[シーケンシャル ワークフロー ビュー \(レガシ\)](../workflow-designer/sequential-workflow-views-legacy.md)」を参照してください。  
  
## 参照  
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)   
 [シーケンシャル ワークフロー ビュー \(レガシ\)](../workflow-designer/sequential-workflow-views-legacy.md)