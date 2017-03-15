---
title: "チュートリアル : トランザクションのデータの保存 | Microsoft Docs"
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
  - "データ [Visual Studio], 保存 (トランザクションに)"
  - "保存 (データを)"
  - "System.Transactions 名前空間"
  - "Transactions 名前空間"
  - "トランザクション, 保存 (データを)"
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# チュートリアル : トランザクションのデータの保存
このチュートリアルでは、<xref:System.Transactions> 名前空間を使用してトランザクションのデータを保存する方法について説明します。  この例では、Northwind サンプル データベースの `Customers` テーブルと `Orders` テーブルを使用します。  
  
## 必須コンポーネント  
 このチュートリアルでは、Northwind サンプル データベースへのアクセスが必要です。  Northwind サンプル データベースのセットアップの詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
## Windows アプリケーションの作成  
 最初に **Windows アプリケーション**を作成します。  
  
#### 新しい Windows プロジェクトを作成するには  
  
1.  Visual Studio の **\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックします。  
  
2.  プロジェクトに SavingDataInATransactionWalkthrough という名前を付けます。  
  
3.  **\[Windows アプリケーション\]** をクリックし、**\[OK\]** をクリックします。  詳細については、「[クライアント アプリケーション](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)」を参照してください。  
  
     **SavingDataInATransactionWalkthrough** プロジェクトが作成されて**ソリューション エクスプローラー**に追加されます。  
  
## データベースのデータ ソースの作成  
 この手順では、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を使用して、Northwind サンプル データベースの `Customers` テーブルと `Orders` テーブルに基づいてデータ ソースを作成します。  
  
#### データ ソースを作成するには  
  
1.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  
  
2.  **\[データ ソース\]** ウィンドウで、**\[新しいデータ ソースの追加\]** をクリックして**データ ソース構成ウィザード**を起動します。  
  
3.  **\[データソースの種類を選択\]** ページで、**\[データベース\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  **\[データ接続の選択\]** ページで、次のいずれかの操作を行います。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
         または  
  
    -   **\[新しい接続\]** を選択して **\[接続の追加\] または \[接続の変更\]** ダイアログ ボックスを表示し、Northwind データベースへの接続を作成します。  
  
5.  データベースにパスワードが必要な場合は、該当するオプションを選択して重要情報を含め、**\[次へ\]** をクリックします。  
  
6.  **\[アプリケーション構成ファイルに接続文字列を保存\]** ページで、**\[次へ\]** をクリックします。  
  
7.  **\[データベース オブジェクトの選択\]** ページの **\[テーブル\]** ノードを展開します。  
  
8.  `Customers` テーブルと `Orders` テーブルを選択し、**\[完了\]** をクリックします。  
  
     プロジェクトに **NorthwindDataSet** が追加され、**\[データ ソース\]** ウィンドウに `Customers` テーブルと `Orders` テーブルが表示されます。  
  
## フォームへのコントロールの追加  
 **\[データ ソース\]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。  
  
#### Windows フォームにデータ バインド コントロールを作成するには  
  
-   **\[データ ソース\]** ウィンドウの **\[Customers\]** ノードを展開します。  
  
-   **\[データ ソース\]** ウィンドウから **Form1** にメインの **\[Customers\]** ノードをドラッグします。  
  
     レコード間をナビゲートするための <xref:System.Windows.Forms.DataGridView> コントロールとツール ストリップ \(<xref:System.Windows.Forms.BindingNavigator>\) がフォームに表示されます。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource>、および <xref:System.Windows.Forms.BindingNavigator> がコンポーネント トレイに表示されます。  
  
-   対応する **\[Orders\]** ノード \(メインの **\[Orders\]** ノードではなく、**\[Fax\]** 列の下の対応する子テーブル ノード\) を **CustomersDataGridView** の下のフォームにドラッグします。  
  
     <xref:System.Windows.Forms.DataGridView> がフォームに表示されます。  コンポーネント トレイに [OrdersTableAdapter](../data-tools/tableadapter-overview.md) と <xref:System.Windows.Forms.BindingSource> が表示されます。  
  
## System.Transactions アセンブリへの参照の追加  
 トランザクションは、<xref:System.Transactions> 名前空間を使用します。  System.Transactions アセンブリへのプロジェクト参照は既定で追加されないため、手動で追加する必要があります。  
  
#### System.Transactions の DLL ファイルへの参照を追加するには  
  
1.  **\[プロジェクト\]** メニューから **\[参照の追加\]** を選択します。  
  
2.  **\[.NET\]** タブの **System.Transactions** を選択し、**\[OK\]** をクリックします。  
  
     **System.Transactions** への参照がプロジェクトに追加されます。  
  
## BindingNavigator の SaveItem ボタンのコードの変更  
 既定では、フォームに最初にドロップされるテーブルのコードは、<xref:System.Windows.Forms.BindingNavigator> の保存ボタンの `click` イベントに追加されます。  追加テーブルを更新する場合は、手動でコードを追加する必要があります。  このチュートリアルでは、保存ボタンの click イベント ハンドラーから既存の保存コードをリファクタリングし、行を追加するか削除するかに応じて、指定された更新機能を提供するメソッドを作成します。  
  
#### 自動生成された保存コードを変更するには  
  
1.  **CustomersBindingNavigator** の **\[保存\]** \(フロッピー ディスクのアイコンのボタン\) をダブルクリックします。  
  
2.  `CustomersBindingNavigatorSaveItem_Click` メソッドを次のコードで置き換えます。  
  
     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]  
  
 関連するデータへの変更を解決する順序は次のとおりです。  
  
-   子レコードを削除します \(この場合は、`Orders` テーブルからレコードを削除します\)。  
  
-   親レコードを削除します \(この場合は、`Customers` テーブルからレコードを削除します\)。  
  
-   親レコードを挿入します \(この場合は、`Customers` テーブルにレコードを挿入します\)。  
  
-   子レコードを挿入します \(この場合は、`Orders` テーブルにレコードを挿入します\)。  
  
#### 既存の注文を削除するには  
  
-   次の `DeleteOrders` メソッドを **Form1** に追加します。  
  
     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-cs[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]  
  
#### 既存の顧客を削除するには  
  
-   次の `DeleteCustomers` メソッドを **Form1** に追加します。  
  
     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-cs[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]  
  
#### 新規顧客を追加するには  
  
-   次の `AddNewCustomers` メソッドを **Form1** に追加します。  
  
     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-cs[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]  
  
#### 新規注文を追加するには  
  
-   次の `AddNewOrders` メソッドを **Form1** に追加します。  
  
     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-cs[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]  
  
## アプリケーションの実行  
  
#### アプリケーションを実行するには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
## 参照  
 [トランザクションと同時実行](../Topic/Transactions%20and%20Concurrency.md)   
 [Oracle 分散トランザクション](../Topic/Oracle%20Distributed%20Transactions.md)   
 [方法 : トランザクションを使用してデータを保存する](../data-tools/save-data-by-using-a-transaction.md)   
 [SQL Server と System.Transactions の統合](../Topic/System.Transactions%20Integration%20with%20SQL%20Server.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)