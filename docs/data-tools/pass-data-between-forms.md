---
title: "チュートリアル: Windows フォーム間でのデータの受け渡し | Microsoft Docs"
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
  - "データ [Visual Studio], 渡す (フォーム間での)"
  - "フォーム, 渡す (データを)"
  - "チュートリアル [Visual Studio], データ"
  - "チュートリアル [Windows フォーム], データ"
  - "Windows フォーム, チュートリアル"
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# チュートリアル: Windows フォーム間でのデータの受け渡し
このチュートリアルでは、フォーム間でデータを渡す手順について説明します。  Northwind の Customers テーブルと Orders テーブルを使用して、1 つのフォームで顧客を選択し、選択した顧客の注文が 2 番目のフォームで表示されるようにします。  このチュートリアルでは、最初のフォームからデータを受け取るもう 1 つのフォームにメソッドを作成する方法を示します。  
  
> [!NOTE]
>  このチュートリアルでは、フォーム間でデータを渡す 1 つの方法についてのみ説明します。  フォームにデータを渡す他の方法として、データを受け取る 2 番目のコンストラクターを作成する方法や、最初のフォームからのデータで設定できるパブリック プロパティを作成する方法もあります。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   新しい **Windows アプリケーション** プロジェクトを作成します。  
  
-   [データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を使用して、データセットを作成して構成します。  
  
-   **\[データ ソース\]** ウィンドウから項目をドラッグしたときにフォーム上に作成するコントロールを選択します。  詳細については、「[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)」を参照してください。  
  
-   **\[データ ソース\]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。  
  
-   データを表示するグリッドのある 2 番目のフォームを作成します。  
  
-   特定の顧客の注文をフェッチする TableAdapter クエリを作成します。  
  
-   フォーム間でデータを渡します。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスします。  詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
## Windows アプリケーションの作成  
  
#### 新しい Windows プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューで新しいプロジェクトを作成します。  
  
2.  プロジェクトに `PassingDataBetweenForms` という名前を付けます。  
  
3.  **\[Windows フォーム アプリケーション\]** をクリックし、**\[OK\]** をクリックします。  詳細については、「[クライアント アプリケーション](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)」を参照してください。  
  
     **PassingDataBetweenForms** プロジェクトが作成され、**ソリューション エクスプローラー**に追加されます。  
  
## データ ソースの作成  
  
#### データ ソースを作成するには  
  
1.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  
  
2.  **\[データ ソース\]** ウィンドウで、**\[新しいデータ ソースの追加\]** をクリックして**データ ソース構成ウィザード**を起動します。  
  
3.  **\[データソースの種類を選択\]** ページで、**\[データベース\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  **\[データベース モデルの選択\]** ページで、**\[データセット\]** が指定されていることを確認し、**\[次へ\]** をクリックします。  
  
5.  **\[データ接続の選択\]** ページで、次のいずれかの操作を行います。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
         または  
  
    -   **\[新しい接続\]** を選択して **\[接続の追加\] または \[接続の変更\]** ダイアログ ボックスを表示します。  
  
6.  データベースにパスワードが必要であり、重要情報を含めるオプションを有効にする場合は、このオプションを選択し、**\[次へ\]** をクリックします。  
  
7.  **\[アプリケーション構成ファイルに接続文字列を保存\]** ページで、**\[次へ\]** をクリックします。  
  
8.  **\[データベース オブジェクトの選択\]** ページの **\[テーブル\]** ノードを展開します。  
  
9. **Customers** テーブルと **Orders** テーブルを選択し、**\[完了\]** をクリックします。  
  
     プロジェクトに **NorthwindDataSet** が追加され、**\[データ ソース\]** ウィンドウに **Customers** テーブルと Orders テーブルが表示されます。  
  
## 最初のフォーム \(Form1\) の作成  
 **\[データ ソース\]** ウィンドウから **Customers** ノードをフォームにドラッグして、データ バインド グリッド \(<xref:System.Windows.Forms.DataGridView> コントロール\) を作成します。  
  
#### フォームにデータ バインド グリッドを作成するには  
  
-   **\[データ ソース\]** ウィンドウから **Form1** にメインの **\[Customers\]** ノードをドラッグします。  
  
     <xref:System.Windows.Forms.DataGridView> と、レコード間を移動するためのツール ストリップ \(<xref:System.Windows.Forms.BindingNavigator>\) が **Form1** 上に表示されます。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource>、および <xref:System.Windows.Forms.BindingNavigator> がコンポーネント トレイに表示されます。  
  
## 2 番目のフォーム \(Form2\) の作成  
  
#### データの渡し先となる 2 番目のフォームを作成するには  
  
1.  **\[プロジェクト\]** メニューから **\[Windows フォームの追加\]** を選択します。  
  
2.  名前を既定の **Form2** のままにして、**\[追加\]** をクリックします。  
  
3.  **\[データ ソース\]** ウィンドウから **Form2** にメインの **\[Orders\]** ノードをドラッグします。  
  
     <xref:System.Windows.Forms.DataGridView> と、レコード間を移動するためのツール ストリップ \(<xref:System.Windows.Forms.BindingNavigator>\) が **Form2** 上に表示されます。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource>、および <xref:System.Windows.Forms.BindingNavigator> がコンポーネント トレイに表示されます。  
  
4.  コンポーネント トレイから **OrdersBindingNavigator** を削除します。  
  
     **Form2** から **OrdersBindingNavigator** が消えます。  
  
## Form1 で選択した顧客の注文を読み込む TableAdapter クエリの Form2 への追加  
  
#### TableAdapter クエリを作成するには  
  
1.  **ソリューション エクスプローラー**で、**NorthwindDataSet.xsd** ファイルをダブルクリックします。  
  
2.  **\[OrdersTableAdapter\]** を右クリックし、**\[クエリの追加\]** を選択します。  
  
3.  **\[SQL ステートメントを使用する\]** を既定のオプションのままにして、**\[次へ\]** をクリックします。  
  
4.  **\[複数行を返す SELECT\]** を既定のオプションのままにして、**\[次へ\]** をクリックします。  
  
5.  `CustomerID` に基づいて `Orders` を返すために、クエリに WHERE 句を追加します。  クエリは次のようになります。  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  データベースに対してパラメーターの構文が正しいことを確認します。  たとえば、Microsoft Access では、WHERE 句は `WHERE CustomerID = ?` のようになります。  
  
6.  **\[次へ\]** をクリックします。  
  
7.  **\[DataTable にデータを格納する\]** の **\[メソッド名\]** に「`FillByCustomerID`」と入力します。  
  
8.  **\[DataTable を返す\]** オプションをオフにして、**\[次へ\]** をクリックします。  
  
9. **\[完了\]** をクリックします。  
  
## データの渡し先となる Form2 のメソッドの作成  
  
#### データの渡し先となるメソッドを作成するには  
  
1.  **Form2** を右クリックし、**\[コードの表示\]** を選択して**コード エディター**で **Form2** を開きます。  
  
2.  **Form2** の `Form2_Load` メソッドの後に次のコードを追加します。  
  
     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-cs[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]  
  
## データを渡し Form2 を表示する Form1 のメソッドの作成  
  
#### Form2 にデータを渡すメソッドを作成するには  
  
1.  **Form1** の Customer データ グリッドを右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  **\[プロパティ\]** ウィンドウで、**\[イベント\]** をクリックします。  
  
3.  **CellDoubleClick** イベントをダブルクリックします。  
  
     コード エディターが表示されます。  
  
4.  メソッド定義を次のサンプルのように更新します。  
  
     [!code-cs[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]  
  
## アプリケーションを実行する  
  
#### アプリケーションを実行するには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
-   **Form1** で顧客レコードをダブルクリックして、その顧客の注文を表示する **Form2** を開きます。  
  
## 次の手順  
 フォーム間でデータを渡した後に、アプリケーションの要件に応じてさらに操作を追加して実行できます。  このチュートリアルで行うことができる拡張には次のものがあります。  
  
-   データセットを編集し、データベース オブジェクトの追加または削除を行います。  詳細については、「[方法 : データセットを編集する](../Topic/How%20to:%20Edit%20a%20Dataset.md)」を参照してください。  
  
-   データベースにデータを戻して保存する機能を追加します。  詳細については、「[方法 : データセットの変更をデータベースに保存する](../Topic/How%20to:%20Save%20Dataset%20Changes%20to%20a%20Database.md)」を参照してください。  
  
## 参照  
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)   
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)