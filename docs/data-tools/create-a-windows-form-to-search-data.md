---
title: "チュートリアル: データを検索する Windows フォームの作成 | Microsoft Docs"
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
  - "データ [Visual Studio], パラメーター化 (クエリを)"
  - "データ [Visual Studio], 検索"
  - "パラメーター, 表示 (フィルター処理されたデータを)"
  - "Windows フォーム, 表示 (データを)"
  - "Windows フォーム, 検索 (データを)"
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 28
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# チュートリアル: データを検索する Windows フォームの作成
一般的なアプリケーションのシナリオでは、選択したデータをフォーム上に表示します。  たとえば、特定の顧客の注文、特定の注文の明細などを表示する場合があります。  このシナリオでは、ユーザーがフォームに情報を入力した後、ユーザーの入力をパラメーターとして使用してクエリが実行されます。つまり、パラメーター クエリに基づいてデータが選択されます。  クエリは、ユーザーが入力した条件を満たすデータのみを返します。  ここでは、特定の都市にいる顧客を返すクエリを作成する方法、およびユーザー インターフェイスを変更して、ユーザーが都市の名前を入力してクエリを実行するボタンを押すことができるようにする方法について説明します。  
  
 パラメーター クエリを使用することにより、データベースが最も得意とする作業 \(レコードの迅速なフィルター処理\) をデータベースに任せることができるため、アプリケーションの効率が高まります。  一方、データベース テーブル全体を要求し、それをネットワークを通じて転送し、アプリケーション ロジックを使用して必要なレコードを見つける場合は、アプリケーションが低速になり、効率が低下する可能性があります。  
  
 [ダイアログ ボックス](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)を使って、TableAdapter \(およびパラメーター値を受け取ってクエリを実行するコントロール\) にパラメーター クエリを追加できます。  このダイアログ ボックスを開くには、**\[データ\]** メニュー \(または TableAdapter スマート タグ\) の **\[クエリの追加\]** をクリックします。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   新しい **Windows アプリケーション** プロジェクトを作成します。  
  
-   [データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を使用して、アプリケーションにデータ ソースを作成して構成します。  
  
-   [ウィンドウ](../Topic/Data%20Sources%20Window.md)で、ドロップ タイプの項目を設定します。  詳細については、「[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)」を参照してください。  
  
-   **\[データ ソース\]** ウィンドウからフォームに項目をドラッグし、データを表示するコントロールを作成します。  
  
-   データを表示するコントロールをフォームに追加します。  
  
-   [ダイアログ ボックス](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)での設定を完了します。  
  
-   フォームにパラメーターを入力し、パラメーター クエリを実行します。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスします。  詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
## Windows アプリケーションの作成  
 最初に **Windows アプリケーション**を作成します。  この手順ではプロジェクトへの名前の割り当てはオプションですが、後でこのプロジェクトを保存するため、プロジェクトに名前を付けます。  
  
#### 新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューで新しいプロジェクトを作成します。  
  
2.  プロジェクトに `WindowsSearchForm` という名前を付けます。  
  
3.  **\[Windows アプリケーション\]** をクリックし、**\[OK\]** をクリックします。  詳細については、「[クライアント アプリケーション](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)」を参照してください。  
  
     **WindowsSearchForm** プロジェクトが作成されて**ソリューション エクスプローラー**に追加されます。  
  
## データ ソースの作成  
 この手順では、**データ ソース構成**ウィザードを使用して、データベースからデータ ソースを作成します。  接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。  Northwind サンプル データベースのセットアップの詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
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
  
## フォームの作成  
 **\[データ ソース\]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。  
  
#### フォームにデータ バインド コントロールを作成するには  
  
1.  **\[データ ソース\]** ウィンドウの **\[Customers\]** ノードを展開します。  
  
2.  **\[Customers\]** ノードを **\[データ ソース\]** ウィンドウからフォームにドラッグします。  
  
     <xref:System.Windows.Forms.DataGridView> と、レコード間を移動するためのツール ストリップ \(<xref:System.Windows.Forms.BindingNavigator>\) がフォーム上に表示されます。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource>、および <xref:System.Windows.Forms.BindingNavigator> がコンポーネント トレイに表示されます。  
  
## クエリへのパラメーター \(検索機能\) の追加  
 [ダイアログ ボックス](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)を使用して元のクエリに WHERE 句を追加できます。  
  
#### パラメーター クエリとコントロールを作成してパラメーターを入力するには  
  
1.  <xref:System.Windows.Forms.DataGridView> コントロールを選択し、**\[データ\]** メニューの **\[クエリの追加\]** をクリックします。  
  
2.  [ダイアログ ボックス](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)の **\[新しいクエリ名\]** に「`FillByCity`」と入力します。  
  
3.  **\[クエリ テキスト\]** 領域でクエリに `WHERE City = @City` を追加します。  
  
     クエリは次のようになります。  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Access データ ソースと OleDb データ ソースは疑問符 "?" を使用してパラメーターを表すため、WHERE 句は `WHERE City = ?` のようになります。  
  
4.  **\[OK\]** をクリックして **\[検索条件ビルダー\]** ダイアログ ボックスを閉じます。  
  
     **FillByCityToolStrip** がフォームに追加されます。  
  
## アプリケーションのテスト  
 アプリケーションを実行すると、パラメーターを入力として取得できる状態のフォームが開きます。  
  
#### アプリケーションをテストするには  
  
1.  F5 キーを押してアプリケーションを実行します。  
  
2.  **\[City\]** ボックスに「London」と入力し、**\[FillByCity\]** をクリックします。  
  
     データ グリッドに、パラメーターの条件を満たす顧客が取得されます。  この例では、**\[City\]** 列の値が **London** の顧客だけがデータ グリッドに表示されます。  
  
## 次の手順  
 アプリケーションの要件に応じて、パラメーター付きのフォームを作成した後に、追加の操作を実行できます。  このチュートリアルで行うことができる拡張には次のものがあります。  
  
-   関連するデータを表示するコントロールを追加します。  詳細については、「[方法: 関連するデータを Windows フォーム アプリケーションに表示する](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)」を参照してください。  
  
-   データセットを編集し、データベース オブジェクトの追加または削除を行います。  詳細については、「[方法 : データセットを編集する](../Topic/How%20to:%20Edit%20a%20Dataset.md)」を参照してください。  
  
## 参照  
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)   
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [BindingSource コンポーネントの概要](../Topic/BindingSource%20Component%20Overview.md)   
 [BindingNavigator コントロールの概要](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)