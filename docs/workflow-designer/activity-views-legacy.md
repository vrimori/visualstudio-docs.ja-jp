---
title: ワークフロー デザイナーのアクティビティ ビュー (レガシ)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d3453ecefece93f593c3d4ebbc261e4332815da
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970335"
---
# <a name="activity-views-legacy"></a>アクティビティ ビュー (レガシ)

Windows Workflow Foundation (WF)、元のワークフローで構成されるを提供するアクティビティの多くが、従来の Windows ワークフロー デザイナーで使用できるいくつかのデザイン ビューがあります。 アクティビティ デザイナーをドラッグすると、**ツールボックス**およびその後、デザイン サーフェイスにいずれかを使用してさまざまなデザイン ビューを切り替えることができます、アクティビティを選択するたびに、**ワークフロー**メニューかを選択した活動を右クリックします。 さらに、選択したアクティビティの名前の上にポインタを移動すると、ドロップダウン タブのセットが表示され、これを使ってさまざまなビューに切り替えることができます。

すべての活動が少なくとも 1 つのビューです。これからアクティビティ デザイナーをドラッグすると表示されている既定のビュー、**ツールボックス**デザイン サーフェイスにします。 このアクティビティの既定の表示として利用可能な **[アクティビティ タイプ] の表示**オプション メニューおよびタブで、たとえば、 **並列の表示**です。 ほとんどのアクティビティには他にもビューがあり、ビューの種類はアクティビティによってさまざまに異なります。 たとえば、 [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)アクティビティは補正ビューおよび[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)アクティビティにはイベント ビューです。 Windows Workflow Foundation に付属しているアクティビティの多くが**キャンセル ハンドラーの**と**エラー**ビューをビューのデザイン、 [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)および[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)それらに関連付けられています。

各ビューの名前と説明の一覧を次の表に示します。

|メニュー/タブ オプション|説明|
|----------------------|-----------------|
|**[アクティビティ タイプ] の表示**|このメニュー オプションまたはタブ オプションをクリックすると、選択したアクティビティの既定のビューがグラフィック表示されます。|
|**キャンセル ハンドラーの表示**|このメニュー オプションまたはタブ オプション ビューを[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)選択したアクティビティに関連付けられています。|
|**エラー ハンドラーの表示**|このメニュー オプションまたはタブ オプション ビューを[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)選択したアクティビティに関連付けられています。|
|**補正ハンドラの表示**|このメニュー オプションまたはタブ オプション ビューを[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) 、選択したに関連付けられている[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)です。|
|**イベント ハンドラーの表示**|このメニュー オプションまたはタブ オプション ビューを[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) 、選択したに関連付けられている、 [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)です。|

同様のビューについては、次を参照してください。[シーケンシャル ワークフロー ビュー (レガシ)](../workflow-designer/sequential-workflow-views-legacy.md)です。

## <a name="see-also"></a>関連項目

- [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)
- [シーケンシャル ワークフロー ビュー (レガシ)](../workflow-designer/sequential-workflow-views-legacy.md)