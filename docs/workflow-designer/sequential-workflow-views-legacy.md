---
title: "シーケンシャル ワークフロー ビュー (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "シーケンシャル ワークフロー ビュー"
  - "シーケンシャル ワークフロー, ビュー"
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# シーケンシャル ワークフロー ビュー (レガシ)
[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] は従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] を備えており、これを使用すると、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とすることができます。  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] で、使い慣れた [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ユーザー インターフェイスを使用して [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションをグラフィカルに作成できます。[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションは、アクティビティと呼ばれるワークフロー プロセス ステップで構成されます。ワークフローを作成するには、それぞれのアクティビティ デザイナーを **\[ツールボックス\]** からデザイン サーフェイスにドラッグして、デザイン サーフェイス上にアクティビティを作成します。  
  
 シーケンシャル ワークフロー \([SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)\) を作成するときには、ワークフローの 3 つのビューを使用できます。これらのビューには、**\[ワークフロー\]** メニューおよびデザイン サーフェイスのコンテキスト メニューからアクセスできます。  
  
 各ビューの名前と説明の一覧を次の表に示します。  
  
|メニュー\/タブ オプション|説明|  
|--------------------|--------|  
|**View SequentialWorkflow**|デザイン サーフェイスを右クリックし、コンテキスト メニューの **\[View SequentialWorkflow\]** オプションをクリックすると、**シーケンシャル ワークフロー** ビューが表示されます。ここには、アクティビティに基づくシーケンシャル ワークフローがグラフィカルに表示されます。または、**\[ワークフロー\]** メニューの **\[View SequentialWorkflow\]** をクリックします。|  
|**キャンセル ハンドラーの表示**|デザイン サーフェイスを右クリックし、コンテキスト メニューの **\[キャンセル ハンドラーの表示\]** オプションをクリックすると、**シーケンシャル ワークフロー** ビューが表示されます。ここには、ワークフローに関連した [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) アクティビティが表示されます。または、**\[ワークフロー\]** メニューの **\[キャンセル ハンドラーの表示\]** をクリックします。|  
|**エラー ハンドラーの表示**|デザイン サーフェイスを右クリックし、コンテキスト メニューの **\[エラー ハンドラーの表示\]** オプションをクリックすると、**エラー** ビューが表示されます。ここには、ワークフローに関連した [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) アクティビティが表示されます。または、**\[ワークフロー\]** メニューから **\[View Fault Handler\]** をクリックします。|  
  
 同様のビューの詳細については、「[アクティビティ ビュー \(レガシ\)](../workflow-designer/activity-views-legacy.md)」を参照してください。  
  
## 参照  
 [アクティビティ ビュー \(レガシ\)](../workflow-designer/activity-views-legacy.md)   
 [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)   
 [ワークフロー作成モード](http://go.microsoft.com/fwlink?LinkID=65014)