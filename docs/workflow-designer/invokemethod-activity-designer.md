---
title: "InvokeMethod アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.InvokeMethod.UI"
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# InvokeMethod アクティビティ デザイナー
**InvokeMethod** デザイナーは、<xref:System.Activities.Statements.InvokeMethod> アクティビティを作成および構成するために使用します。  
  
## InvokeMethod アクティビティ  
 <xref:System.Activities.Statements.InvokeMethod> は、指定されたオブジェクトまたは型のパブリック メソッドを呼び出します。  
  
### InvokeMethod アクティビティ デザイナーの使用  
 **InvokeMethod** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[プリミティブ\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **InvokeMethod** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、InvokeMethod という既定の <xref:System.Activities.Activity.DisplayName%2A> を持つ <xref:System.Activities.Statements.InvokeMethod> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> は、**InvokeMethod** アクティビティ デザイナーのヘッダーか、プロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。  
  
### InvokeMethod プロパティ  
 次の表に、<xref:System.Activities.Statements.InvokeMethod> のプロパティと、それをデザイナーで使用する方法を示します。これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]のデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.InvokeMethod> アクティビティの表示名。既定値は InvokeMethod です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|必須|アクティビティの実行時に呼び出すメソッドの名前。呼び出されたメソッドは、**public** として宣言する必要があります。このプロパティは、デザイナー画面で設定することもできます。これは必須プロパティです。|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|省略可|呼び出されたメソッドのパラメーター コレクション。パラメーターは、メソッド シグネチャ内で出現する順序でコレクションに追加する必要があります。プロパティ グリッドで、**\[パラメーター\]** フィールド内の省略記号ボタンをクリックすると、このプロパティを設定できる **\[パラメーター\]** ダイアログが表示されます。**\[引数の作成\]** ボタンをクリックしてパラメーターを追加します。|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|省略可|メソッド呼び出しの戻り値。|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|必須|メソッドが非同期で呼び出されるかどうかを指定します。既定値は **False** です。|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|省略可|呼び出すメソッドを格納するオブジェクト。このプロパティは、デザイナー画面で設定することもできます。<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> および <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> のいずれかを設定する必要があります。|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|省略可|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> の型。このプロパティは、デザイナー画面で編集できます。このプロパティは、メソッド呼び出しが静的である場合にのみ設定する必要があります。|  
  
 C\# の **out** パラメーター \(たとえば `Method1(out myParam)),`\) としてパラメーターを渡すには、**InOutArgument** ではなく、**OutArgument** を使用する必要があります。  
  
 **TargetObject** または **Result** という引数を含むメソッドは、<xref:System.Activities.Statements.InvokeMethod> アクティビティを使用して呼び出すことはできません。これは、<xref:System.Activities.Statements.InvokeMethod> アクティビティによって <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>、<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>、および <xref:System.Activities.Statements.InvokeMethod.Result%2A> が <xref:System.Activities.Activity.CacheMetadata%2A> に登録されるためです。  
  
 <xref:System.Activities.Activity.CacheMetadata%2A> にパラメーターを登録するアルゴリズムは次のとおりです。  
  
1.  <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 引数を登録します。  
  
2.  <xref:System.Activities.Statements.InvokeMethod.Result%2A> 引数を登録します。  
  
3.  <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> コレクションを繰り返し処理し、各引数を登録します。  
  
 結果の例外の種類は <xref:System.Activities.InvalidWorkflowException> となり、メッセージの内容は、"'InvokeMethod': 名前が 'TargetObject' の変数 RuntimeArgument または DelegateArgument は既に存在します" となります。名前は、環境スコープ内で一意であることが必要です。  
  
 この制限は、<xref:System.Activities.Statements.InvokeMethod.TargetType%2A> および <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> には適用されません。これらはワークフロー引数ではなく、したがって、<xref:System.Activities.Activity.CacheMetadata%2A> メソッド内の <xref:System.Activities.Statements.InvokeMethod> アクティビティの<xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> コレクションに登録されないためです。  
  
## 参照  
 [プリミティブ](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)