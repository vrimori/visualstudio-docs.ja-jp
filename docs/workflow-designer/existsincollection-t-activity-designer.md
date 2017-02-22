---
title: "ExistsInCollection&lt;T&gt; アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ExistsInCollection`1.UI"
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ExistsInCollection&lt;T&gt; アクティビティ デザイナー
**ExistsInCollection\<T\>** アクティビティ デザイナーは、<xref:System.Activities.Statements.ExistsInCollection%601> アクティビティを作成および構成するために使用します。  
  
## ExistsInCollection\<T\> アクティビティ  
 <xref:System.Activities.Statements.ExistsInCollection%601> アクティビティでは、指定した項目が特定のコレクションに存在するかどうかを確認します。  
  
### ExistsInCollection\<T\> アクティビティ デザイナーの使用  
 **ExistsInCollection\<T\>** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[コレクション\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **ExistsInCollection\<T\>** アクティビティ デザイナーを **\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、ExistsInCollection\<Int32\> という既定の <xref:System.Activities.Activity.DisplayName%2A> を持つ <xref:System.Activities.Statements.ExistsInCollection%601> アクティビティが作成されます \(*TypeArgument* の既定値は **Int32** です。プロパティ グリッドで変更できます\)。<xref:System.Activities.Activity.DisplayName%2A> 値は、**ExistsInCollection\<T\>** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。他のプロパティは、プロパティ グリッドで編集する必要があります。  
  
### ExistsInCollection\<T\> のプロパティ  
 次の表に、<xref:System.Activities.Statements.ExistsInCollection%601> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.ExistsInCollection%601> アクティビティの表示名。既定値は ExistsInCollection\<Int32\> です。<xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|必須|Collection\<T\> に追加する項目。この項目は、*TypeArgument* 型の *T* 型です。項目を指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|必須|項目の追加先のコレクション。このコレクションは、**ICollection\<TypeArgument\>.** 型です。コレクションを指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
|*TypeArgument*|必須|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型。既定では、この *TypeArgument* 型は **Int32** に設定されています。型を変更するには、プロパティ グリッドのコンボ ボックスで、*TypeArgument* の値を変更します。|  
|<xref:System.Activities.Activity%601.Result%2A>|省略可|指定した項目がコレクション内に存在するかどうかを示す値。結果にバインドする変数を指定するには、プロパティ グリッドで Visual Basic 変数を入力します。|  
  
## 参照  
 [コレクション](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)