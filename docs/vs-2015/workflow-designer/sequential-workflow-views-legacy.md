---
title: シーケンシャル ワークフロー ビュー (レガシ) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 46c37ec7f3813078b9e70076bf92e6d0e1b86453
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547465"
---
# <a name="sequential-workflow-views-legacy"></a>シーケンシャル ワークフロー ビュー (レガシ)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] は従来の [!INCLUDE[wfd1](../includes/wfd1-md.md)] を備えており、これを使用すると、[!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] または [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] を対象とすることができます。  
  
 [!INCLUDE[wfd2](../includes/wfd2-md.md)] では、使い慣れた [!INCLUDE[wf](../includes/wf-md.md)] ユーザー インターフェイスを使用して [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] アプリケーションをグラフィカルに作成できます。 [!INCLUDE[wf](../includes/wf-md.md)] アプリケーションは、アクティビティと呼ばれるワークフロー プロセス ステップで構成されます。 ワークフローを作成するから、それぞれのアクティビティ デザイナーをドラッグしてデザイン サーフェイスにアクティビティを作成**ツールボックス**デザイン サーフェイスにします。  
  
 これは、シーケンシャル ワークフローを作成する場合、 [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)ワークフローの 3 つのビューは使用できます。 これらのビューはからアクセスできる、**ワークフロー**メニューおよびデザイン サーフェイスのコンテキスト メニュー。  
  
 各ビューの名前と説明の一覧を次の表に示します。  
  
|メニュー/タブ オプション|説明|  
|----------------------|-----------------|  
|**View SequentialWorkflow**|デザイン サーフェスと選択を右クリックし、 **View SequentialWorkflow** 、コンテキスト メニューを表示するオプション、**シーケンシャル ワークフロー**ビューがアクティビティに基づく表示グラフィックシーケンシャル ワークフローの表現。 選択または**View SequentialWorkflow**から、**ワークフロー**メニュー。|  
|**キャンセル ハンドラーの表示**|デザイン サーフェスと選択を右クリックし、 **キャンセル ハンドラーの**、コンテキスト メニューを表示するオプション、**シーケンシャル ワークフロー**表示、表示する、 [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)ワークフローに関連付けられているアクティビティ。 選択または**キャンセル ハンドラーの**から、**ワークフロー**メニュー。|  
|**エラー ハンドラー**|デザイン サーフェスと選択を右クリックし、 **エラー ハンドラー** 、コンテキスト メニューを表示するオプション、**エラー**表示、表示する、 [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)ワークフローに関連付けられているアクティビティ。 選択または**エラー ハンドラー**から、**ワークフロー**メニュー。|  
  
 同様のビューについての詳細については、次を参照してください。[アクティビティ ビュー (レガシ)](../workflow-designer/activity-views-legacy.md)します。  
  
## <a name="see-also"></a>関連項目  
 [アクティビティ ビュー (レガシ)](../workflow-designer/activity-views-legacy.md)   
 [従来のワークフロー プロジェクトを作成します。](../workflow-designer/creating-legacy-workflow-projects.md)   
 [ワークフロー作成モード](http://go.microsoft.com/fwlink?LinkID=65014)