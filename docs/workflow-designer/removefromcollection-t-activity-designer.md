---
title: "RemoveFromCollection&lt;T&gt; アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.RemoveFromCollection`1.UI"
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# RemoveFromCollection&lt;T&gt; アクティビティ デザイナー
**RemoveFromCollection\<T\>** アクティビティ デザイナーは、<xref:System.Activities.Statements.RemoveFromCollection%601> アクティビティを作成および構成するために使用します。  
  
## RemoveFromCollection\<T\> アクティビティ  
 <xref:System.Activities.Statements.RemoveFromCollection%601> アクティビティは、指定した項目を特定のコレクションから削除します。  
  
### RemoveFromCollection\<T\> アクティビティ デザイナーの使用  
 **RemoveFromCollection\<T\>** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[コレクション\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **RemoveFromCollection\<T\>** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、RemoveFromCollection\<Int32\> という既定の <xref:System.Activities.Activity.DisplayName%2A> を持つ <xref:System.Activities.Statements.RemoveFromCollection%601> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> 値は、**RemoveFromCollection\<T\>** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。他のプロパティは、プロパティ グリッドで編集する必要があります。  
  
### RemoveFromCollection\<T\> のプロパティ  
 次の表に、<xref:System.Activities.Statements.RemoveFromCollection%601> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|------------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.RemoveFromCollection%601> アクティビティの省略可能な表示名。既定値は、RemoveFromCollection\<Int32\> です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|必須|**Collection\<T\>** に追加する項目。この項目は、*TypeArgument* 型の *T* 型です。項目を指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|必須|項目の追加先のコレクション。このコレクションは、**ICollection\<TypeArgument\>.** 型です。コレクションを指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
|*TypeArgument*|必須|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型。既定では、この *TypeArgument* 型は **Int32** に設定されています。型を変更するには、プロパティ グリッドのコンボ ボックスで、*TypeArgument* の値を変更します。|  
|<xref:System.Activities.Activity%601.Result%2A>|省略可|指定した項目がコレクションから削除されたかどうかを示す値。結果にバインドする変数を指定するには、プロパティ グリッドで変数を入力します。|  
  
## 参照  
 [コレクション](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)