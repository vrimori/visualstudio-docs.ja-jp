---
title: "Rethrow アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Rethrow.UI"
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Rethrow アクティビティ デザイナー
**Rethrow** アクティビティ デザイナーは、<xref:System.Activities.Statements.Rethrow> アクティビティを作成および構成するために使用します。  
  
## Rethrow アクティビティ  
 <xref:System.Activities.Statements.Rethrow> アクティビティでは、以前にスローされた例外をスローします。このアクティビティは、<xref:System.Activities.Statements.TryCatch> アクティビティの <xref:System.Activities.Statements.Catch> ハンドラーでのみ使用できます。  
  
### ReThrow アクティビティ デザイナーの使用  
 **Rethrow** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[エラー処理\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の左側にある **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **Rethrow** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、Throw という既定の **DisplayName** を持つ <xref:System.Activities.Statements.Rethrow> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> 値は、**Rethrow** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。  
  
### Rethrow のプロパティ  
 次の表に、<xref:System.Activities.Statements.Rethrow> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.ReThrow> アクティビティの表示名を指定します \(省略可能\)。既定値は Rethrow です。|  
  
## 参照  
 [コレクション](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)