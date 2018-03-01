---
title: "Assign アクティビティ デザイナー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: bb816aee41f86e2cbdc71e93b78f1a9e09249a00
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="assign-activity-designer"></a>Assign アクティビティ デザイナー
**割り当てる**アクティビティ デザイナーを使用して作成し、構成、<xref:System.Activities.Statements.Assign>アクティビティ。  
  
## <a name="the-assign-activity"></a>Assign アクティビティ  
 <xref:System.Activities.Statements.Assign> アクティビティで、変数または引数に値を割り当てます。  
  
### <a name="using-the-assign-activity-designer"></a>Assign アクティビティ デザイナーの使用  
 **割り当てる**アクティビティ デザイナーは含まれて、**プリミティブ**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス** タブ (または、選択**ツールボックス**から、**ビュー**メニューまたは CTRL + ALT + X です)。  
  
 **割り当てる**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面でアクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>です。 これを作成、 <xref:System.Activities.Statements.Assign> 、既定値を持つアクティビティ**DisplayName**の割り当て。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、**割り当てる**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。  
  
### <a name="the-assign-properties"></a>Assign のプロパティ  
 次の表に、<xref:System.Activities.Statements.Assign> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集できます。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Assign> アクティビティの表示名。 既定値は Assign です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|<xref:System.Activities.Statements.Assign.Value%2A> を割り当てる変数または引数。 有効な Visual Basic 識別子を指定する必要があります。 プロパティを設定するには、Visual Basic の式を入力、**に**ボックスに、**割り当てる**アクティビティ デザイナーまたはプロパティ グリッドでします。|  
|<xref:System.Activities.Statements.Assign.Value%2A>|True|変数に割り当てられる値。 設定する、 <xref:System.Activities.Statements.Assign.Value%2A>、Visual Basic の式を入力、**値**ボックスに、**割り当てる**アクティビティ デザイナーまたはプロパティ グリッドでします。|  
  
## <a name="see-also"></a>参照  
 [プリミティブ](../workflow-designer/primitives-activity-designers.md)   
 [遅延](../workflow-designer/delay-activity-designer.md)   
 [メソッドの呼び出し](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)