---
title: ワークフロー デザイナーのシーケンシャル ワークフロー ビュー (レガシ)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce1217ea629ae0301b72b444161d61db4fe448b1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976020"
---
# <a name="sequential-workflow-views-legacy"></a>シーケンシャル ワークフロー ビュー (レガシ)

Visual Studio 2010 では、.NET Framework version 3.5、または、WinFX をターゲットに使用できる従来の Windows ワークフロー デザイナーを提供します。

ワークフロー デザイナーでは、Windows Workflow Foundation (WF) を使い慣れた Visual Studio ユーザー インターフェイスを使用してアプリケーションをグラフィカルに作成する方法を提供します。 Windows Workflow Foundation (WF) アプリケーションは、アクティビティと呼ばれるワークフロー プロセスの手順で構成されます。 ワークフローを作成するには、デザイン サーフェイス上にアクティビティを作成、それぞれのアクティビティ デザイナーをドラッグすることで**ツールボックス**デザイン サーフェイスにします。

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