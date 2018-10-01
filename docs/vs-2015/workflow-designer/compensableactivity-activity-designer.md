---
title: CompensableActivity アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 89d95d2b3e58f88687fc9236c387cc31bfc5ddbf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535734"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity アクティビティ デザイナー
**CompensableActivity**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.CompensableActivity>アクティビティ。  
  
## <a name="the-compensableactivity-activity"></a>CompensableActivity アクティビティ  
 <xref:System.Activities.Statements.CompensableActivity> で、正常に完了した後に確認または補正できる作業単位を定義します。  
  
### <a name="using-the-compensableactivity-activity-designer"></a>CompensableActivity アクティビティ デザイナーの使用  
 **CompensableActivity**アクティビティ デザイナーが記載されて、**トランザクション**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**  タブの左側にある、 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X)。  
  
 **CompensableActivity**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス任意の場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>します。 この操作により、CompensableActivity という既定の <xref:System.Activities.Statements.CompensableActivity> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、 **CompensableActivity**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。  
  
### <a name="the-compensableactivity-properties"></a>CompensableActivity のプロパティ  
 次の表に、<xref:System.Activities.Statements.CompensableActivity> のプロパティと、デザイナーでのその使用方法を示します。 <xref:System.Activities.Activity.DisplayName%2A> プロパティと <xref:System.Activities.Activity%601.Result%2A> プロパティはプロパティ グリッドで編集できますが、それ以外のプロパティは[!INCLUDE[wfd2](../includes/wfd2-md.md)]画面で編集する必要があります。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CompensableActivity> アクティビティの省略可能な表示名。 既定値は CompensableActivity です。|  
|<xref:System.Activities.Activity%601.Result%2A>|False|<xref:System.Activities.Statements.CompensableActivity> の戻り値を指定します。 このプロパティは、プロパティ グリッドで編集する必要があります。|  
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|補正、取り消し、および確認の各ロジックの提供対象のアクティビティを指定します。 追加する、<xref:System.Activities.Statements.CompensableActivity.Body%2A>アクティビティからアクティビティのドロップ、**ツールボックス**に、**本文**ボックスに、 **CompensableActivity**アクティビティ デザイナーのヒント テキスト"Dropここにアクティビティ"。|  
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|取り消しの際に実行されるアクティビティを指定します。 アクティビティを追加するからデザイナーをドロップ、**ツールボックス**に、 **CancellationHandler**ボックスに、 **CompensableActivity**アクティビティ デザイナーのヒント テキスト"Dropここにアクティビティ"。|  
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|<xref:System.Activities.Statements.CompensableActivity.Body%2A> アクティビティの補正を行うときに実行されるアクティビティを指定します。 このハンドラーは、<xref:System.Activities.Statements.Compensate> アクティビティを使用して明示的に呼び出すことができます。<br /><br /> アクティビティ デザイナーをドロップ アクティビティを追加する、**ツールボックス**に、 **CompensationHandler**ボックスに、 **CompensableActivity**アクティビティ デザイナーのヒント テキスト"ここにアクティビティをドロップ"。|  
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|<xref:System.Activities.Statements.CompensableActivity.Body%2A> アクティビティを確認するときに実行されるアクティビティを指定します。 このハンドラーは、<xref:System.Activities.Statements.Confirm> アクティビティを使用して明示的に呼び出すことができます。<br /><br /> アクティビティ デザイナーをドロップ アクティビティを追加する、**ツールボックス**に、 **ConfirmationHandler**ボックスに、 **CompensableActivity**アクティビティ デザイナーのヒント テキスト"ここにアクティビティをドロップ"。|  
  
## <a name="see-also"></a>関連項目  
 [トランザクション](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [補正](../workflow-designer/compensate-activity-designer.md)   
 [確認します](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)