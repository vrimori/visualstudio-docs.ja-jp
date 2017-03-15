---
title: "TryCatch アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TryCatch.UI"
  - "System.Activities.Statements.Catch`1.UI"
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# TryCatch アクティビティ デザイナー
**TryCatch** アクティビティ デザイナーは、<xref:System.Activities.Statements.TryCatch> アクティビティを作成および構成するために使用します。  
  
## TryCatch アクティビティ  
 <xref:System.Activities.Statements.TryCatch> アクティビティには、<xref:System.Activities.Statements.TryCatch.Try%2A> アクティビティ、**Catch\<TException\>** のコレクション、および <xref:System.Activities.Statements.TryCatch.Finally%2A> アクティビティが含まれます。**TException** 型の <xref:System.Activities.Statements.Catch%601> には、<xref:System.Activities.Statements.Catch%601.ExceptionType%2A> および <xref:System.Activities.Statements.Catch%601.Action%2A> が含まれます。これらの組み合わせによって、標準的な例外ベースのエラー処理機構が実装されます。<xref:System.Activities.Statements.TryCatch> アクティビティは、対応する <xref:System.Activities.Statements.TryCatch.Try%2A> アクティビティの実行を試みます。<xref:System.Activities.Statements.TryCatch.Try%2A> アクティビティから例外がスローされた場合、<xref:System.Activities.Statements.TryCatch> アクティビティは、その **Catch\<TException\>** コレクションを使用して例外を照合します。一致が見つかった場合は、対応する **Catch\<TException\>** の <xref:System.Activities.Statements.Catch%601.Action%2A> が、例外のエラー処理ロジックとして実行されます。<xref:System.Activities.Statements.TryCatch.Try%2A> セクションのアクティビティまたは  <xref:System.Activities.Statements.TryCatch.Catches%2A> のアクティビティが正常に完了した場合、<xref:System.Activities.Statements.TryCatch> アクティビティは  <xref:System.Activities.Statements.TryCatch.Finally%2A> アクティビティを実行します。[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][例外](../Topic/Exceptions.md).  
  
### TryCatch アクティビティ デザイナーの使用  
 **TryCatch** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[エラー処理\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の左側にある **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **TryCatch** アクティビティ デザイナーを **\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の任意の画面 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、TryCatch の既定の <xref:System.Activities.Activity.DisplayName%2A> を持つ <xref:System.Activities.Statements.TryCatch> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> 値は、**TryCatch** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。それ以外のプロパティは、**TryCatch** アクティビティ デザイナーの画面上で編集する必要があります。  
  
 **TryCatch** デザイナーの右上隅にある展開ボタンをクリックすると、**\[Try\]**、**\[Catch\]**、および **\[Finally\]** の各ボックスが、展開されたビューに表示されます。catch を追加するには、**TryCatch** デザイナーの **\[新しい catch の追加\]** ボタンをクリックします。このボタンが、型のコンボ ボックスに変化します。例外の型を選択し、Enter キーを押して catch を追加します。**Catch** を追加すると、catch の領域が展開されるので、そこにアクティビティをドロップして catch の実行ロジックを定義できます。展開された catch 領域の右側にはテキスト ボックスが表示されます。このテキスト ボックスを使用して、例外変数に名前を付けることができます。この例外変数は、同じ **Catch** 内のアクティビティでのみ使用できます。  
  
 **TryCatch** デザイナーでは、**Catch** の編集はサポートされません。例外の型を変更する場合は、**Catch** を削除してから、新たに追加する必要があります。**Catch** を選択して直接削除できるほか、右クリックして表示されるコンテキスト メニューの **\[削除\]** メニューを使用して削除することもできます。  
  
### TryCatch のプロパティ  
 次の表に、<xref:System.Activities.Statements.TryCatch> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.TryCatch> アクティビティの表示名を指定します \(省略可能\)。既定値は TryCatch です。|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|<xref:System.Activities.Statements.TryCatch> を実行すると、このアクティビティが最初に実行されます。|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|<xref:System.Activities.Statements.TryCatch.Try%2A> アクティビティから例外がスローされた場合にチェックされる **Catch** 要素のコレクションです。<br /><br /> <xref:System.Activities.Statements.TryCatch.Catches%2A> にアクティビティを少なくとも 1 つ追加するか、または、<xref:System.Activities.Statements.TryCatch.Finally%2A> ブロックにアクティビティを追加する必要があります。|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|<xref:System.Activities.Statements.TryCatch.Try%2A> および  <xref:System.Activities.Statements.TryCatch.Catches%2A> コレクション内の必要なアクティビティがすべて完了した段階で実行されるアクティビティ。<br /><br /> <xref:System.Activities.Statements.TryCatch.Catches%2A> にアクティビティを少なくとも 1 つ追加するか、または、<xref:System.Activities.Statements.TryCatch.Finally%2A> ブロックにアクティビティを追加する必要があります。|  
  
## 参照  
 [コレクション](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)