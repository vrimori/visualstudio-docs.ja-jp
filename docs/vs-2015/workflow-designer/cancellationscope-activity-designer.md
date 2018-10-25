---
title: CancellationScope アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 125e9fd934ce40d2a6633daa62b817628306daa3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229893"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope アクティビティ デザイナー
**CancellationScope**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.CancellationScope>アクティビティ。  
  
## <a name="the-cancellationscope-activity"></a>CancellationScope アクティビティ  
 <xref:System.Activities.Statements.CancellationScope> アクティビティを使用すると、実行のアクティビティと、そのアクティビティの取り消しロジックを指定できます。  
  
### <a name="using-the-cancellationscope-activity-designer"></a>CancellationScope アクティビティ デザイナーの使用  
 **CancellationScope**アクティビティ デザイナーが記載されて、**トランザクション**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**のタブ、 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X)。  
  
 **CancellationScope**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス任意の場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>します。 この操作により、CancellationScope という既定の <xref:System.Activities.Statements.CancellationScope> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、 **CancellationScope**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。  
  
### <a name="the-cancellationscope-properties"></a>CancellationScope プロパティ  
 次の表に、<xref:System.Activities.Statements.CancellationScope> のプロパティと、デザイナーでのその使用方法を示します。 <xref:System.Activities.Activity.DisplayName%2A> プロパティはプロパティ グリッドで編集できますが、それ以外のプロパティは[!INCLUDE[wfd2](../includes/wfd2-md.md)]画面で編集する必要があります。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> アクティビティの省略可能な表示名。 既定では、CancellationScope です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|取り消しロジックの対象となるアクティビティを指定します。 追加する、<xref:System.Activities.Statements.CancellationScope.Body%2A>アクティビティからアクティビティのドロップ、**ツールボックス**に、**本文**ボックスに、 **CancellationScope**アクティビティ デザイナーのヒント テキスト"Dropここにアクティビティ"。|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|取り消しの際に実行されるアクティビティを指定します。 追加する、<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>アクティビティからアクティビティのドロップ、**ツールボックス**に、 **CancellationHandler**ボックスに、 **CancellationScope**アクティビティ デザイナーのヒントテキスト"アクティビティここにドロップします。|  
  
## <a name="see-also"></a>関連項目  
 [トランザクション](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [補正](../workflow-designer/compensate-activity-designer.md)   
 [確認します](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)