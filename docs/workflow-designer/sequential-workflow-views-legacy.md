---
title: "シーケンシャル ワークフロー ビュー (レガシ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 8b54fbb37d33bdb6d4e397c81ad85bffd39b221f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sequential-workflow-views-legacy"></a>シーケンシャル ワークフロー ビュー (レガシ)
[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] は従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] を備えており、これを使用すると、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とすることができます。  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] では、使い慣れた [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] ユーザー インターフェイスを使用して [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] アプリケーションをグラフィカルに作成できます。 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションは、アクティビティと呼ばれるワークフロー プロセス ステップで構成されます。 ワークフローを作成するには、デザイン サーフェイス上にアクティビティを作成、それぞれのアクティビティ デザイナーをドラッグすることで**ツールボックス**デザイン サーフェイスにします。  
  
 これは、シーケンシャル ワークフローを作成する場合、 [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)ワークフローの 3 つのビューを利用できます。 これらのビューからアクセス可能な**ワークフロー**メニューおよびデザイン サーフェイスのコンテキスト メニューからです。  
  
 各ビューの名前と説明の一覧を次の表に示します。  
  
|メニュー/タブ オプション|説明|  
|----------------------|-----------------|  
|**View SequentialWorkflow**|デザイン画面と選択を右クリックし、 **View SequentialWorkflow** 、コンテキスト メニューを表示するオプション、**シーケンシャル ワークフロー**ビューがアクティビティに基づく表示グラフィックシーケンシャル ワークフローの表現。 選択または**View SequentialWorkflow**から、**ワークフロー**メニュー。|  
|**キャンセル ハンドラーの表示**|デザイン画面と選択を右クリックし、 **キャンセル ハンドラーの**、コンテキスト メニューを表示するオプション、**シーケンシャル ワークフロー**ビューが、 [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)ワークフローに関連付けられたアクティビティ。 選択または**キャンセル ハンドラーの**から、**ワークフロー**メニュー。|  
|**エラー ハンドラーの表示**|デザイン画面と選択を右クリックし、 **View Fault Handler** 、コンテキスト メニューを表示するオプション、**エラー**ビューが、 [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)ワークフローに関連付けられたアクティビティ。 選択または**View Fault Handler**から、**ワークフロー**メニュー。|  
  
 ようなビューの詳細については、次を参照してください。[アクティビティ ビュー (レガシ)](../workflow-designer/activity-views-legacy.md)です。  
  
## <a name="see-also"></a>参照  
 [アクティビティ ビュー (レガシ)](../workflow-designer/activity-views-legacy.md)   
 [従来のワークフロー プロジェクトを作成します。](../workflow-designer/creating-legacy-workflow-projects.md)   
 [ワークフロー作成モード](http://go.microsoft.com/fwlink?LinkID=65014)