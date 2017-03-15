---
title: "ClearCollection&lt;T&gt; アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ClearCollection`1.UI"
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ClearCollection&lt;T&gt; アクティビティ デザイナー
**ClearCollection\<T\>** アクティビティ デザイナーは、<xref:System.Activities.Statements.ClearCollection%601> アクティビティを作成および構成するために使用します。  
  
## ClearCollection\<T\> アクティビティ  
 <xref:System.Activities.Statements.ClearCollection%601> アクティビティで、指定したすべての項目のコレクションをクリアします。  
  
### ClearCollection\<T\> アクティビティ デザイナーの使用  
 **ClearCollection\<T\>** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[コレクション\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **ClearCollection\<T\>** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、ClearCollection\<Int32\> という既定の <xref:System.Activities.Activity.DisplayName%2A> を持つ <xref:System.Activities.Statements.ClearCollection%601> アクティビティが作成されます \(*TypeArgument* の既定値は **Int32** です。プロパティ グリッドで変更できます\)。<xref:System.Activities.Activity.DisplayName%2A> 値は、**ClearCollection\<T\>** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。他のプロパティは、プロパティ グリッドで編集する必要があります。  
  
### ClearCollection\<T\> のプロパティ  
 次の表に、<xref:System.Activities.Statements.ClearCollection%601> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.ClearCollection%601> アクティビティの表示名を指定します \(省略可能\)。既定値は、ClearCollection\<Int32\> です。<xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|必須|クリアする項目のコレクションを指定します。このコレクションは、**ICollection\<TypeArgument\>.** 型です。コレクションを指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
|*TypeArgument*|必須|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型を指定します。既定では、この *TypeArgument* 型は **Int32** に設定されています。型を変更するには、プロパティ グリッドのコンボ ボックスで、*TypeArgument* の値を変更します。|  
  
## 参照  
 [コレクション](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)