---
title: ワークフロー デザイナー - TransactedReceiveScope アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c7f5c4cd48cc98d58da278ac53c1a829d15c43cd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976853"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope アクティビティ デザイナー

**TransactedReceiveScope**デザイナーを使用して作成し、構成、<xref:System.ServiceModel.Activities.TransactedReceiveScope>アクティビティ。

## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope アクティビティ

<xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティを使用すると、ワークフローまたはディスパッチャーによって作成されたサーバー トランザクションにトランザクションをフローできます。

### <a name="using-the-transactedreceivescope-activity-designer"></a>TransactedReceiveScope アクティビティ デザイナーの使用
 **TransactedReceiveScope**アクティビティ デザイナーは含まれて、**メッセージング**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**ワークフロー デザイナーのタブ (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X です)。

 **TransactedReceiveScope**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**し、アクティビティを通常配置している場所に、ワークフロー デザイナー画面にドロップします。 これを作成、 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 、既定値を持つアクティビティ**DisplayName** TransactedReceiveScope のです。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **TransactedReceiveScope**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

 **TransactedReceiveScope**デザイナーが含まれています**要求**と**本文**ボックス。 これらは、<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> プロパティを構成するために使用します。このプロパティでは、<xref:System.ServiceModel.Activities.Receive> アクティビティと、他の <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> を指定する <xref:System.Activities.Activity> プロパティを指定します。 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> によって、トランザクションが作成されます。 その後、トランザクションはこのスコープのアンビエント トランザクションになり、<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> のスコープ内のあらゆるアクティビティは、このトランザクション内で実行されます。

### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope のプロパティ
 次の表に、<xref:System.ServiceModel.Activities.TransactedReceiveScope> のプロパティと、デザイナーでのその使用方法を示します。 これら<xref:System.Activities.Activity.DisplayName%2A>プロパティ グリッドで、またはワークフロー デザイナー画面で、プロパティを編集できますが、他のユーザーは、デザイン画面で編集する必要があります。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティの省略可能な表示名。 既定値は、TransactedReceiveScope です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> 名は必須ではありませんが、使用することをお勧めします。|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|削除操作を行う、<xref:System.ServiceModel.Activities.Receive>にアクティビティ、**要求**アクティビティ デザイナー画面上のブロックです。|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|削除操作を行う、<xref:System.Activities.Activity>に、**本文**アクティビティ デザイナー画面上のブロックです。|

## <a name="see-also"></a>関連項目

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [受信](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [送信](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)