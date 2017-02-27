---
title: "InvokeDelegate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "InvokeDelegate Designer"
  - "System.Activities.Statements.InvokeDelegate.UI"
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 3
---
# InvokeDelegate
**InvokeDelegate** デザイナーは、<xref:System.Activities.Statements.InvokeDelegate> アクティビティを作成および構成するために使用します。  
  
## InvokeDelegate アクティビティ  
 <xref:System.Activities.Statements.InvokeDelegate> はパブリック デリゲートを呼び出します。  
  
### InvokeDelegate アクティビティ デザイナーの使用  
 **InvokeDelegate** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[プリミティブ\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **InvokeDelegate** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、InvokeDelegate という既定の <xref:System.Activities.Activity.DisplayName%2A> を持つ <xref:System.Activities.Statements.InvokeDelegate> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> は、**InvokeDelegate** アクティビティ デザイナーのヘッダーか、プロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。  
  
### InvokeDelegate プロパティ  
 次の表に、<xref:System.Activities.Statements.InvokeDelegate> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]のデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.InvokeDelegate> アクティビティの表示名。既定値は InvokeDelegate です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|アクティビティの実行時に呼び出す <xref:System.Activities.Statements.ActivityDelegate> の名前。このプロパティは、デザイナー画面で設定することもできます。これは必須プロパティです。|  
|<xref:System.Activities.Statements.InvokeMethod.DelegateArguments%2A>|False|呼び出されたデリゲートの引数コレクション。キーは <xref:System.Activities.Statements.ActivityDelegate> の <xref:System.Activities.Statements.ActivityDelegateParameter> オブジェクトの名前であり、値は、式が評価され対応する <xref:System.Activities.Statements.ActivityDelegateParameter> オブジェクトに割り当てられる引数です。プロパティ グリッドで、**DelegateArguments** フィールド内の省略記号ボタンをクリックすると、このプロパティを設定できる **\[DelegateArguments\]** ダイアログが表示されます。**引数の作成**フィールドをクリックして引数を追加します。|  
  
## 参照  
 [ワークフロー デザイナーでアクティビティ デリゲートを定義および使用する方法](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)