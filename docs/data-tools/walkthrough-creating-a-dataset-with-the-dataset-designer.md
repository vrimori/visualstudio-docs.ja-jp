---
title: "チュートリアル : データセット デザイナーでのデータセットの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "データ [Visual Studio], データセット デザイナー"
  - "データセット デザイナー, チュートリアル"
  - "データセット [Visual Basic], 作成"
  - "データセット [Visual Basic], チュートリアル"
  - "XML スキーマ, 作成 (データセットの)"
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# チュートリアル : データセット デザイナーでのデータセットの作成
このチュートリアルでは、**データセット デザイナー**を使用してデータセットを作成します。  ここでは、新しいプロジェクトを作成し、そのプロジェクトに新しい **Dataset** 項目を追加します。  ウィザードを使用しないで、データベース内のテーブルに基づいてテーブルを作成する方法について説明します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   新しい **Windows アプリケーション** プロジェクトを作成します。  
  
-   空の **DataSet** 項目をプロジェクトに追加します。  
  
-   **データセット デザイナー**を使用してデータセットを作成することにより、アプリケーションにデータ ソースを作成して設定します。  
  
-   **サーバー エクスプローラー**に Northwind データベースへの接続を作成します。  
  
-   データベース内のテーブルに基づいて、データセットに TableAdapter を持つテーブルを作成します。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベース \(SQL Server または Access バージョン\) にアクセスします。  詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
## 新しい Windows アプリケーション プロジェクトの作成  
  
#### 新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューで新しいプロジェクトを作成します。  
  
2.  **\[プロジェクトの種類\]** ペインでプログラミング言語を選択します。  
  
3.  **\[テンプレート\]** ペインの **\[Windows アプリケーション\]** をクリックします。  
  
4.  プロジェクトに `DatasetDesignerWalkthrough` という名前を付け、**\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で**ソリューション エクスプローラー**にプロジェクトが追加され、デザイナーに新しいフォームが表示されます。  
  
## アプリケーションへの新しいデータセットの追加  
  
#### プロジェクトに新しいデータセット項目を追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
     **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスの **\[テンプレート\]** ボックスで、**\[データセット\]** をクリックします。  
  
3.  データセットに `NorthwindDataset` という名前を付け、**\[追加\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でプロジェクトに **NorthwindDataset.xsd** という名前のファイルが追加され、**データセット デザイナー**でこのファイルが開かれます。  
  
## サーバー エクスプローラーでのデータ接続の作成  
  
#### Northwind データベースへの接続を作成するには  
  
1.  **\[表示\]** メニューの **\[サーバー エクスプローラー\]** をクリックします。  
  
2.  **サーバー エクスプローラー**で、**\[データベースへの接続\]** をクリックします。  
  
3.  Northwind サンプル データベースへの接続を作成します。  
  
    > [!NOTE]
    >  このチュートリアルでは、SQL Server バージョンまたは Access バージョンの Northwind に接続できます。  
  
## データセットへのテーブルの作成  
 ここでは、データセットにテーブルを追加する方法について説明します。  
  
#### Customers テーブルを作成するには  
  
1.  **サーバー エクスプローラー**で作成したデータ接続を展開し、**\[テーブル\]** ノードを展開します。  
  
2.  **サーバー エクスプローラー**から**データセット デザイナー**に **Customers** テーブルをドラッグします。  
  
     **Customers** データ テーブルと **CustomersTableAdapter** がデータセットに追加されます。  
  
#### Orders テーブルを作成するには  
  
-   **サーバー エクスプローラー**から**データセット デザイナー**に **Orders** テーブルをドラッグします。  
  
     **Orders** データ テーブル、**OrdersTableAdapter**、および **Customers** テーブルと **Orders** テーブル間のリレーションシップが、データセットに追加されます。  
  
#### OrderDetails テーブルを作成するには  
  
-   **サーバー エクスプローラー**から**データセット デザイナー**に **Order Details** テーブルをドラッグします。  
  
     **Order Details** データ テーブル、**Order DetailsTableAdapter**、および **Orders** テーブルと **Order Details** テーブル間のリレーションシップが、データセットに追加されます。  
  
## 次の手順  
  
### アプリケーションに機能を追加するには  
  
-   データセットを保存します。  
  
-   **\[データ ソース\]** ウィンドウの項目を選択し、フォームにドラッグします。  詳細については、「[Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)」を参照してください。  
  
-   TableAdapter に他のクエリを追加します。  詳細については、「[方法 : TableAdapter クエリを作成する](../data-tools/how-to-create-tableadapter-queries.md)」を参照してください。  
  
-   データセット内のデータ テーブルの <xref:System.Data.DataTable.ColumnChanging> イベントまたは <xref:System.Data.DataTable.RowChanging> イベントに検証ロジックを追加します。  詳細については、「[データセットのデータの検証](../data-tools/validate-data-in-datasets.md)」を参照してください。  
  
## 参照  
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)