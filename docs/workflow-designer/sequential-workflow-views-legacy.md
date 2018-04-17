---
title: シーケンシャル ワークフロー ビュー (レガシ) |Microsoft ドキュメント
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6b42ba9c1c9f7dbe2beb4a741501967e4968508
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sequential-workflow-views-legacy"></a>シーケンシャル ワークフロー ビュー (レガシ)
[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 使用できる従来の Windows ワークフロー デザイナーは、ターゲットに、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)]または[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]です。

 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] では、使い慣れた [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] ユーザー インターフェイスを使用して [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] アプリケーションをグラフィカルに作成できます。 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションは、アクティビティと呼ばれるワークフロー プロセス ステップで構成されます。 ワークフローを作成するには、デザイン サーフェイス上にアクティビティを作成、それぞれのアクティビティ デザイナーをドラッグすることで**ツールボックス**デザイン サーフェイスにします。

 これは、シーケンシャル ワークフローを作成する場合、 [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)ワークフローの 3 つのビューを利用できます。 これらのビューからアクセス可能な**ワークフロー**メニューおよびデザイン サーフェイスのコンテキスト メニューからです。

 各ビューの名前と説明の一覧を次の表に示します。

|メニュー/タブ オプション|説明|
|----------------------|-----------------|
|**View SequentialWorkflow**|デザイン画面と選択を右クリックし、 **View SequentialWorkflow** 、コンテキスト メニューを表示するオプション、**シーケンシャル ワークフロー**ビューがアクティビティに基づく表示グラフィックシーケンシャル ワークフローの表現。 選択または**View SequentialWorkflow**から、**ワークフロー**メニュー。|
|**キャンセル ハンドラーの表示**|デザイン画面と選択を右クリックし、 **キャンセル ハンドラーの**、コンテキスト メニューを表示するオプション、**シーケンシャル ワークフロー**ビューが、 [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)ワークフローに関連付けられたアクティビティ。 選択または**キャンセル ハンドラーの**から、**ワークフロー**メニュー。|
|**エラー ハンドラーの表示**|デザイン画面と選択を右クリックし、 **View Fault Handler** 、コンテキスト メニューを表示するオプション、**エラー**ビューが、 [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)ワークフローに関連付けられたアクティビティ。 選択または**View Fault Handler**から、**ワークフロー**メニュー。|

 ようなビューの詳細については、次を参照してください。[アクティビティ ビュー (レガシ)](../workflow-designer/activity-views-legacy.md)です。

## <a name="see-also"></a>関連項目

- [アクティビティ ビュー (レガシ)](../workflow-designer/activity-views-legacy.md)
- [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)
- [ワークフロー作成モード](http://go.microsoft.com/fwlink?LinkID=65014)