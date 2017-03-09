---
title: "方法 : TableAdapter クエリを編集する | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbData.Microsoft.VSDesigner.DataSource.DbSource"
  - "vbdata.Microsoft.VSDesigner.DataSource.DbSource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [Visual Studio], TableAdapter"
  - "編集 (クエリを)"
  - "クエリ [Visual Basic], 編集"
  - "TableAdapter, 編集 (クエリを)"
ms.assetid: aac7b7b4-bd91-4225-95d4-a07643568c43
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 方法 : TableAdapter クエリを編集する
TableAdapter クエリの編集には、データセット デザイナーの [TableAdapter クエリの構成ウィザード](../data-tools/editing-tableadapters.md)を使用します。  TableAdapter クエリがアプリケーションの要件に合わなくなった場合は、そのクエリを変更する必要があります  \(または、TableAdapter で別のクエリを作成できます。  新しいクエリの追加方法の詳細については、「[方法 : TableAdapter クエリを作成する](../data-tools/how-to-create-tableadapter-queries.md)」を参照してください\)。  
  
> [!NOTE]
>  **TableAdapter クエリの構成ウィザード**の代わりに [TableAdapter 構成ウィザード](../Topic/TableAdapter%20Configuration%20Wizard.md)が開く場合は、TableAdapter に追加したクエリではなく、TableAdapter のメインの `Fill` クエリを選択している可能性があります。  TableAdapter のメインの `Fill` クエリの編集方法については、「[方法 : TableAdapter を編集する](../Topic/How%20to:%20Edit%20TableAdapters.md)」を参照してください。  
  
 ![複数のクエリがある TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")  
  
### TableAdapter クエリを編集するには  
  
1.  **データセット デザイナー**でデータセットを開きます。  詳細については、「[方法 : データセット デザイナーでデータセットを開く](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)」を参照してください。  
  
2.  編集する TableAdapter クエリを選択します。  
  
3.  TableAdapter クエリを右クリックし、**\[構成\]** をクリックします。  
  
     **TableAdapter クエリの構成ウィザード**が開き、クエリやそのクエリのストアド プロシージャを変更できます。  
  
4.  **TableAdapter クエリの構成ウィザード**で必要な変更を入力します。  詳細については、「[TableAdapter クエリの構成ウィザード](../data-tools/editing-tableadapters.md)」を参照してください。  
  
## 参照  
 [TableAdapter](../Topic/TableAdapters.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)   
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)