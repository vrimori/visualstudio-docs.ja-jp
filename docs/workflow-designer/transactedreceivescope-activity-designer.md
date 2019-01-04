---
title: ワークフロー デザイナー - TransactedReceiveScope アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e4860eb391f4aab0f15eaa0536b248140c1e5770
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914930"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope アクティビティ デザイナー

**TransactedReceiveScope**を作成および構成デザイナーを使用する<xref:System.ServiceModel.Activities.TransactedReceiveScope>アクティビティ。

## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope アクティビティ

<xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティを使用すると、ワークフローまたはディスパッチャーによって作成されたサーバー トランザクションにトランザクションをフローできます。

### <a name="using-the-transactedreceivescope-activity-designer"></a>TransactedReceiveScope アクティビティ デザイナーの使用

アクセス、 **TransactedReceiveScope**内のアクティビティ デザイナー、**メッセージング**のカテゴリ、**ツールボックス**します。 **TransactedReceiveScope**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**とアクティビティを通常配置して任意の場所は、ワークフロー デザイナー画面にドロップします。 これを作成、 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 、既定値は、アクティビティ**DisplayName** TransactedReceiveScope の。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **TransactedReceiveScope**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

**TransactedReceiveScope**デザイナーに**要求**と**本文**ボックス。 これらは、<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> プロパティを構成するために使用します。このプロパティでは、<xref:System.ServiceModel.Activities.Receive> アクティビティと、他の <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> を指定する <xref:System.Activities.Activity> プロパティを指定します。 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> によって、トランザクションが作成されます。 その後、トランザクションはこのスコープのアンビエント トランザクションになり、<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> のスコープ内のあらゆるアクティビティは、このトランザクション内で実行されます。

### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope のプロパティ

次の表に、<xref:System.ServiceModel.Activities.TransactedReceiveScope> のプロパティと、デザイナーでのその使用方法を示します。 これら<xref:System.Activities.Activity.DisplayName%2A>プロパティ グリッドで、またはワークフロー デザイナー画面で、プロパティを編集できますが、デザイン画面で、他のユーザー編集する必要があります。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティの省略可能な表示名。 既定値は、TransactedReceiveScope です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> 名は必須ではありませんが、使用することをお勧めします。|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|削除操作を行う、<xref:System.ServiceModel.Activities.Receive>にアクティビティ、**要求**アクティビティ デザイナー画面にブロックします。|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|削除操作を行う、<xref:System.Activities.Activity>に、**本文**アクティビティ デザイナー画面にブロックします。|

## <a name="see-also"></a>関連項目

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)