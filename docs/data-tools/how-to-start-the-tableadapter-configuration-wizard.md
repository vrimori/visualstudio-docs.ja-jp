---
title: "方法 :TableAdapter 構成ウィザードを開始する | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "TableAdapter 構成ウィザード"
  - "TableAdapter, 構成ウィザード"
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 方法 :TableAdapter 構成ウィザードを開始する
**TableAdapter 構成ウィザード**を使用して、厳密に型指定されたデータセット内内で TableAdapter を作成および編集します。  このウィザードでは、ウィザードに入力した SQL ステートメントまたはデータベース内の既存のストアド プロシージャに基づいて TableAdapter が作成されます。  このウィザードを使用すると、ウィザードに入力した SQL ステートメントに基づいて、データベース内に新しいストアド プロシージャを作成することもできます。  
  
### TableAdapter 構成ウィザードを開始して新しい TableAdapter を作成するには  
  
1.  **データセット デザイナー**でデータセットを開きます。  詳細については、「[方法 : データセット デザイナーでデータセットを開く](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)」を参照してください。  
  
    > [!NOTE]
    >  プロジェクトにデータセットがない場合は、「[方法 : 型指定されたデータセットを作成する](../data-tools/create-and-configure-datasets-in-visual-studio.md)」を参照してください。  
  
2.  新しい TableAdapter を作成する場合は、**ツールボックス**の **\[データセット\]** タブから**データセット デザイナー**に、**\[TableAdapter\]** オブジェクトをドラッグします。  
  
3.  **\[データ接続の選択\]** ページで、現在利用できる接続の一覧からデータ接続を選択するか、**\[新しい接続\]** を選択して、新しい接続を作成します。  
  
### TableAdapter 構成ウィザードを開始して既存の TableAdapter を編集するには  
  
1.  **データセット デザイナー**でデータセットを開きます。  詳細については、「[方法 : データセット デザイナーでデータセットを開く](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)」を参照してください。  
  
2.  **データセット デザイナー**で TableAdapter を右クリックし、**\[構成\]** を選択します。  TableAdapter の元の設定方法に応じて、ウィザードで **\[SQL ステートメントの生成\]** ページまたは **\[コマンドを既存のストアド プロシージャにバインドする\]** ページが開きます。  
  
3.  ウィザードの指示に従います。  
  
## 参照  
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)   
 [方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [方法 : Windows フォーム BindingSource コンポーネントで ADO.NET データを並べ替える\/フィルター処理する](../Topic/How%20to:%20Sort%20and%20Filter%20ADO.NET%20Data%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [方法 : Windows フォーム BindingSource コンポーネントを使用してルックアップ テーブルを作成する](../Topic/How%20to:%20Create%20a%20Lookup%20Table%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)