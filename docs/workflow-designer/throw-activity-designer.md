---
title: "Throw アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Throw.UI"
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Throw アクティビティ デザイナー
**Throw** アクティビティ デザイナーは、<xref:System.Activities.Statements.Throw> アクティビティを作成および構成するために使用します。  
  
## Throw アクティビティ  
 <xref:System.Activities.Statements.Throw> アクティビティによって例外がスローされます。  
  
### Throw アクティビティ デザイナーの使用  
 **Throw** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[エラー処理\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の左側にある **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **Throw** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、Throw という既定の **DisplayName** を持つ <xref:System.Activities.Statements.Throw> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> 値は、**Throw** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。この <xref:System.Activities.Statements.Throw.Exception%2A> プロパティは、プロパティ グリッドで編集する必要があります。  
  
### Throw プロパティ  
 次の表に、<xref:System.Activities.Statements.Throw> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.Throw> アクティビティの表示名を指定します \(省略可能\)。既定値は Throw です。|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|必須|スローされる例外。この例外は、<xref:System.Exception> から派生していることが必要です。例外を指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
  
## 参照  
 [コレクション](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw Activity Designer](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)