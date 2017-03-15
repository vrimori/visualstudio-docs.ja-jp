---
title: "チュートリアル : 複数のクエリによる TableAdapter の作成 | Microsoft Docs"
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
  - "データ [Visual Studio], TableAdapter"
  - "データ [Visual Studio], チュートリアル"
  - "クエリ [Visual Studio], TableAdapter"
  - "TableAdapter クエリ, 作成"
  - "TableAdapter, 作成"
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# チュートリアル : 複数のクエリによる TableAdapter の作成
このチュートリアルでは、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を使用してデータセット内に TableAdapter を作成します。  また、[データセット デザイナー](../data-tools/creating-and-editing-typed-datasets.md)内の [TableAdapter クエリの構成ウィザード](../data-tools/editing-tableadapters.md)を使用して、[TableAdapter](../data-tools/tableadapter-overview.md) 内に 2 つ目のクエリを作成する手順についても説明します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   新しい **Windows アプリケーション** プロジェクトを作成します。  
  
-   **データ ソース構成**ウィザードを使用してデータセットを作成することにより、アプリケーションにデータ ソースを作成して設定します。  
  
-   **データセット デザイナー**で新しいデータセットを開きます。  
  
-   **TableAdapter クエリの構成ウィザード**を使用して TableAdapter にクエリを追加します。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベース \(SQL Server または Access バージョン\) にアクセスします。  詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
## 新しい Windows アプリケーションの作成  
 最初に Windows アプリケーションを作成します。  
  
#### 新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で、**\[ファイル\]**\<\/ui\> メニューから新しいプロジェクトを作成します。  
  
2.  **\[プロジェクトの種類\]** ペインでプログラミング言語を選択します。  
  
3.  **\[テンプレート\]** ペインの **\[Windows アプリケーション\]** をクリックします。  
  
4.  プロジェクトに「`TableAdapterQueriesWalkthrough`」という名前を付け、**\[OK\]** をクリックします。  
  
     Visual Studio によって**ソリューション エクスプローラー**にプロジェクトが追加され、デザイナーに新しいフォームが表示されます。  
  
## TableAdapter によるデータベース データ ソースと の作成  
 この手順では、**データ ソース構成**ウィザードを使用して、Northwind サンプル データベースの `Customers` テーブルに基づいてデータ ソースを作成します。  接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。  Northwind サンプル データベースのセットアップの詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
#### データ ソースを作成するには  
  
1.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  
  
2.  **\[データ ソース\]** ウィンドウで、**\[新しいデータ ソースの追加\]** をクリックして**データ ソース構成ウィザード**を起動します。  
  
3.  **\[データソースの種類を選択\]** ページで、**\[データベース\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  **\[データ接続の選択\]** ページで、次のいずれかの操作を行います。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
         または  
  
    -   **\[新しい接続\]** を選択して **\[接続の追加\] または \[接続の変更\]** ダイアログ ボックスを表示します。  
  
5.  データベースにパスワードが必要な場合は、該当するオプションを選択して重要情報を含め、**\[次へ\]** をクリックします。  
  
6.  **\[アプリケーション構成ファイルに接続文字列を保存\]** ページで、**\[次へ\]** をクリックします。  
  
7.  **\[データベース オブジェクトの選択\]** ページの **\[テーブル\]** ノードを展開します。  
  
8.  **Customers** テーブルを選択し、**\[完了\]** をクリックします。  
  
     プロジェクトに **NorthwindDataSet** が追加され、**\[データ ソース\]** ウィンドウに **Customers** テーブルが表示されます。  
  
## データセット デザイナーでデータセットを開く  
  
#### データセット デザイナーでデータセットを開くには  
  
1.  **\[データ ソース\]** ウィンドウの **\[NorthwindDataSet\]** を右クリックします。  
  
2.  ショートカット メニューの **\[デザイナーで DataSet を編集\]** をクリックします。  
  
     **データセット デザイナー**で NorthwindDataset が開きます。  
  
## CustomersTableAdapter への 2 つ目のクエリの追加  
 このウィザードでは、**Customers** データ テーブルと **CustomersTableAdapter** を含むデータセットが作成されています。  ここでは、**CustomersTableAdapter** に 2 つ目のクエリを追加します。  
  
#### CustomersTableAdapter にクエリを追加するには  
  
1.  **ツールボックス**の **\[DataSet\]** タブから **Customers** テーブルに **\[Query\]** をドラッグします。  
  
     [TableAdapter クエリの構成ウィザード](../data-tools/editing-tableadapters.md) が表示されます。  
  
2.  **\[SQL ステートメントを使用する\]** を選択し、**\[次へ\]** をクリックします。  
  
3.  **\[複数行を返す SELECT\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  クエリに次のように WHERE 句を追加します。  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Access バージョンの Northwind を使用している場合は、@City パラメーターを疑問符 \(?\) に置換してください。  \(`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`\)  
  
5.  **\[生成するメソッドの選択\]** ページで **\[DataTable にデータを格納する\]** メソッドに「`FillByCity`」という名前を付けます。  
  
    > [!NOTE]
    >  このチュートリアルでは、**\[DataTable を返す\]** メソッドを使用しないので、このチェック ボックスをオフにするか、既定の名前のままにします。  
  
6.  **\[次へ\]** をクリックし、ウィザードを終了します。  
  
     **FillByCity** クエリが **CustomersTableAdapter** に追加されます。  
  
## 追加のクエリを実行するコードのフォームへの追加  
  
#### クエリを実行するには  
  
1.  **ソリューション エクスプローラー**で **Form1** を選択し、**\[デザイナーの表示\]** をクリックします。  
  
2.  **\[データ ソース\]** ウィンドウから **Form1** に **\[Customers\]** ノードをドラッグします。  
  
3.  **\[表示\]** メニューの **\[コード\]** をクリックしてコード ビューに変更します。  
  
4.  `Form1_Load` イベント ハンドラー内のコードを、`FillByCity` クエリを実行する以下のコードに置き換えます。  
  
     [!CODE [VbRaddataTableAdapters#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#1)]  
  
## アプリケーションの実行  
  
#### アプリケーションを実行するには  
  
-   F5 キーを押します。  
  
-   グリッドに、`City` 値が `Seattle` の顧客が読み込まれます。  
  
## 次の手順  
  
### アプリケーションに機能を追加するには  
  
-   <xref:System.Windows.Forms.TextBox> コントロールおよび <xref:System.Windows.Forms.Button> コントロールを追加し、テキスト ボックスの値をクエリに渡します。  \(`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`\).  
  
-   データセット内のデータ テーブルの <xref:System.Data.DataTable.ColumnChanging> イベントまたは <xref:System.Data.DataTable.RowChanging> イベントに検証ロジックを追加します。  詳細については、「[データセットのデータの検証](../data-tools/validate-data-in-datasets.md)」を参照してください。  
  
## 参照  
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [方法 : TableAdapter を作成する](../data-tools/create-and-configure-tableadapters.md)   
 [方法 : TableAdapter クエリを作成する](../data-tools/how-to-create-tableadapter-queries.md)   
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)