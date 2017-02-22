---
title: "ParallelForEach&lt;T&gt; アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ParallelForEach`1.UI"
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ParallelForEach&lt;T&gt; アクティビティ デザイナー
<xref:System.Activities.Statements.ParallelForEach%601> アクティビティでは、コレクションの要素を列挙し、コレクションの各要素に対して埋め込みステートメントを並列的に \(同じスレッドで非同期的に\) 実行します。このフロー制御アクティビティは、その子アクティビティがアイドル状態になると予想される場合に、<xref:System.Activities.Statements.Sequence> アクティビティの代わりに使用します。  
  
 <xref:System.Activities.Statements.ParallelForEach%601> アクティビティには、ユーザーによって指定された [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 式を保持する <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> プロパティがあります。このプロパティは、各分岐の完了後に、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティによって評価されます。評価結果が **true** の場合、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティは他の分岐を実行せずに完了します。<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> が **true** に評価されない場合は、すべての子アクティビティが完了するまで <xref:System.Activities.Statements.ParallelForEach%601> アクティビティが継続されます。  
  
## ParallelForEach\<T\> アクティビティ  
 <xref:System.Activities.Statements.ParallelForEach%601> はそれ自体の値を列挙し、列挙した値ごとに <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> をスケジュールします。スケジュールされるのは <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> のみです。本文の実行方法は、<xref:System.Activities.Statements.ParallelForEach%601.Body%2A> がアイドル状態になるかどうかによって異なります。  
  
 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> がアイドル状態にならない場合は、スケジュールされたアクティビティがスタックとして扱われるため、逆の順序で実行されます。つまり、最後にスケジュールされたアクティビティが最初に実行されます。たとえば、<xref:System.Activities.Statements.ParallelForEach%601> に {1,2,3,4} というコレクションがあるときに、**WriteLine** を本文として使用して値を書き出すとします。この場合は、4、3、2、1 の順にコンソールに出力されます。これは、**WriteLine** がアイドル状態にならず、スケジュールされた 4 つの **WriteLine** アクティビティがスタックの動作 \(先入れ後出し\) に従って実行されたためです。  
  
 ただし、<xref:System.ServiceModel.Activities.Receive> アクティビティや <xref:System.Activities.Statements.Delay> アクティビティのように、アイドル状態になる可能性のあるアクティビティが <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> に含まれている場合は、それぞれのアクティビティが完了するまで待機する必要はありません。<xref:System.Activities.Statements.ParallelForEach%601> は次のスケジュールされた本文アクティビティに進み、実行を試みます。そのアクティビティもアイドル状態になる場合は、<xref:System.Activities.Statements.ParallelForEach%601> が、さらに次の本文アクティビティに進みます。  
  
### ParallelForEach\<T\> アクティビティ デザイナーの使用  
 **ParallelForEach\<T\>** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[制御フロー\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の左側にある **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら x キーを押します\)。  
  
 **ParallelForEach\<T\>** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティ デザイナーを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(**Sequence** アクティビティ デザイナー内など\) にドロップできます。このアクティビティ デザイナーを[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]にドロップすると、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティが作成されます。既定では、このアクティビティに **ParallelForEach\<Int32\>.** の <xref:System.Activities.Activity.DisplayName%2A> が含まれます。  
  
### ワークフロー デザイナーでの ParallelForEach\<T\> のプロパティ  
 次の表に、最も役に立つ <xref:System.Activities.Statements.ParallelForEach%601> アクティビティのプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|------------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|ヘッダーのアクティビティ デザイナーの表示名を指定します。既定値は **ParallelForEach\<Int32\>** です。この値は、**\[プロパティ\]** グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|省略可|コレクション内の各項目に対して実行するアクティビティ。<xref:System.Activities.Statements.ParallelForEach%601.Body%2A> アクティビティを追加するには、"ここにアクティビティをドロップします" というヒント テキストが表示された **ParallelForEach\<T\>** アクティビティ デザイナーの **\[Body\]** ボックスに、\[ツールボックス\] からアクティビティをドロップします。|  
|**TypeArgument**|True|ジェネリック パラメーター *T* で指定された <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> コレクション内の項目の型。既定では、**TypeArgument** は **Int32** に設定されています。**ParallelForEach\<T\>** アクティビティ デザイナーで型 T を変更するには、プロパティ グリッドの **\[TypeArgument\]** ボックスの値を変更します。|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|必須|反復処理を行う項目のコレクション。<xref:System.Activities.Statements.ParallelForEach%601.Values%2A> を設定するには、"VB の式を入力してください" というヒント テキストが表示された **ForEach\<T\>** アクティビティ デザイナーの **\[値\]** ボックス、または **\[プロパティ\]** ウィンドウの **\[値\]** ボックスに、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の式を入力します。|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||各イテレーションの完了後に評価されます。true であると評価する場合、スケジュールされた保留イテレーションはキャンセルされます。このプロパティが設定されていない場合、スケジュールされたすべてのステートメントは、完了するまで実行されます。|  
  
 既定では、ループ反復子には、item という名前が付けられます。反復子変数の名前は、**ParallelForEach\<T\>** アクティビティ デザイナーの **\[ForEach\]** ボックスで変更できます。ループ反復子は、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティの子の式で使用できます。  
  
## 参照  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)