---
title: ワークフロー デザイナー - CorrelationScope アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d1da881dfb7f7a8c063b94e49198d1b299b2e47b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942050"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope アクティビティ デザイナー

**CorrelationScope**作成および構成するアクティビティ デザイナーが使用される、<xref:System.ServiceModel.Activities.CorrelationScope>暗黙で管理を使用して、子メッセージング アクティビティのアクティビティを<xref:System.ServiceModel.Activities.CorrelationHandle>オブジェクト。

## <a name="the-correlationscope-activity"></a>CorrelationScope アクティビティ

<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> プロパティでは、子メッセージング アクティビティの管理に使用する <xref:System.ServiceModel.Activities.CorrelationHandle> を指定します。 <xref:System.ServiceModel.Activities.Send> に含まれる <xref:System.ServiceModel.Activities.Receive> アクティビティおよび <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> アクティビティは、親 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> アクティビティの <xref:System.ServiceModel.Activities.CorrelationScope> プロパティを使用して関連付けを行うように構成されます。

### <a name="use-the-correlationscope-activity-designer"></a>CorrelationScope アクティビティ デザイナーを使用します。

**CorrelationScope**アクティビティ デザイナーが記載されて、**メッセージング**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**ワークフロー デザイナーの左側にあるタブ。 または、選択**ツールボックス**から、**ビュー**メニューのまたはキーを押して**Ctrl**+**Alt** + **X**します。

**CorrelationScope**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**し、ワークフロー デザイナー画面にドロップします。 これを作成、 <xref:System.ServiceModel.Activities.CorrelationScope> 、既定値は、アクティビティ**DisplayName** CorrelationScope の。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **CorrelationScope**アクティビティ デザイナーまたは、 **DisplayName**のボックス、**プロパティ**ウィンドウ。

指定する、<xref:System.ServiceModel.Activities.CorrelationHandle>子メッセージング アクティビティで使用される、横にある省略記号ボタンを選択して、 **CorrelatesWith**フィールドに**プロパティ**を表示するウィンドウ、**式エディター**  ダイアログ ボックス。 このプロパティは、アクティビティ デザイナー画面で設定することもできます。

相関関係のスコープ内でアクティビティがデザイナーで指定された、**本文**ボックス内、 **CorrelationScope**デザイナー。

### <a name="the-correlationscope-properties"></a>CorrelationScope プロパティ

次の表に、<xref:System.ServiceModel.Activities.CorrelationScope> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティのどちらでも編集**プロパティ**ウィンドウ ワークフロー デザイナー画面で、両方で多くの場合、または。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティの省略可能な表示名。|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|子メッセージング アクティビティの管理に使用する <xref:System.ServiceModel.Activities.CorrelationHandle> を指定します。 このプロパティを設定しない場合は、<xref:System.ServiceModel.Activities.CorrelationScope> に、暗黙の <xref:System.ServiceModel.Activities.CorrelationHandle> が自動的に作成されます。|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|相関関係のスコープ内のアクティビティを指定します。|

## <a name="see-also"></a>関連項目

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)