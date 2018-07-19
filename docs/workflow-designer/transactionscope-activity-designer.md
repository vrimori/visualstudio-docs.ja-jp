---
title: ワークフロー デザイナーの TransactionScope アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7622dc9b926124d0ed2b2ae759beafcbac3a475a
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755799"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope アクティビティ デザイナー

**TransactionScope**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.TransactionScope>アクティビティ。

## <a name="the-transactionscope-activity"></a>TransactionScope アクティビティ

<xref:System.Activities.Statements.TransactionScope> アクティビティでは、含まれているアクティビティを単一のトランザクションで実行します。 <xref:System.Activities.Statements.TransactionScope.Body%2A> アクティビティおよびトランザクションの他のすべての参加要素が正常に完了すると、トランザクションはコミットされます。

### <a name="using-the-transactionscope-activity-designer"></a>TransactionScope アクティビティ デザイナーの使用

アクセス、 **TransactionScope**内のアクティビティ デザイナー、**トランザクション**のカテゴリ、**ツールボックス**します。 **TransactionScope**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**どこにも、アクティビティを通常配置など内に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>します。 この操作により、TransactionScope という既定の <xref:System.Activities.Statements.TransactionScope> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、 **TransactionScope**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-transactionscope-properties"></a>TransactionScope プロパティ

次の表に、<xref:System.Activities.Statements.TransactionScope> のプロパティと、デザイナーでのその使用方法を示します。 <xref:System.Activities.Activity.DisplayName%2A>と<xref:System.Activities.Statements.TransactionScope.Body%2A>プロパティは、ワークフロー デザイナー画面で編集できます。 ただし、他のプロパティは、プロパティ グリッドで編集する必要があります。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TransactionScope> アクティビティの省略可能な表示名。 既定値は、TransactionScope です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|単一のトランザクションで実行するアクティビティを指定します。 追加する、<xref:System.Activities.Statements.TransactionScope.Body%2A>アクティビティからアクティビティのドロップ、**ツールボックス**に、**本文**ボックスに、 **TransactionScope**ヒントのテキスト"にアクティビティをドロップを使用してアクティビティ デザイナーここで"。|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|この <xref:System.Transactions.IsolationLevel> の <xref:System.Activities.Statements.TransactionScope> を指定します。|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|トランザクションが完了するまでの時間間隔を "00:00:00" (時:分:秒) という形式で指定します。 既定値は 1 分 (00:01:00) です。|
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|True|トランザクションが中止した場合にワークフローを中止する必要があるかどうかを示す値を指定します。|

## <a name="see-also"></a>関連項目

- [トランザクション](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [補正](../workflow-designer/compensate-activity-designer.md)
- [確認します](../workflow-designer/confirm-activity-designer.md)