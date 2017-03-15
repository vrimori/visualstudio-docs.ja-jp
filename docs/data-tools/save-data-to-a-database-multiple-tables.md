---
title: "チュートリアル : データベースへのデータの保存 (複数テーブル) | Microsoft Docs"
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
  - "データ [Visual Studio], 保存"
  - "データ [Visual Studio], 更新"
  - "保存 (データを), チュートリアル"
  - "更新 (データセットを), チュートリアル"
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# チュートリアル : データベースへのデータの保存 (複数テーブル)
アプリケーション開発における最も一般的なシナリオの 1 つに、Windows アプリケーションのフォームにデータを表示して編集し、更新したデータをデータベースに返送する操作があります。  このチュートリアルでは、2 つの関連するテーブルのデータを表示するフォームを作成し、レコードを編集して変更内容をデータベースに保存する方法を示します。  この例では、Northwind サンプル データベースの `Customers` テーブルと `Orders` テーブルを使用します。  
  
 アプリケーション内のデータをデータベースに保存するには、TableAdapter の `Update` メソッドを呼び出します。  項目を **\[データ ソース\]** ウィンドウからドラッグすると、データを保存するコードが、フォームにドラッグされた最初のテーブルに自動的に追加されます。  さらに別のテーブルをフォームに追加した場合は、データ保存用のコードを手動で追加する必要があります。  ここでは、複数のテーブルから更新を保存するコードを追加する手順を示します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   新しい **Windows アプリケーション** プロジェクトを作成します。  
  
-   [データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を使用して、アプリケーションにデータ ソースを作成して構成します。  
  
-   [ウィンドウ](../Topic/Data%20Sources%20Window.md)で、項目のコントロールを設定します。  詳細については、「[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)」を参照してください。  
  
-   **\[データ ソース\]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。  
  
-   データセットの各テーブルのいくつかのレコードを変更します。  
  
-   データセット内の更新されたデータをデータベースに返送するコードを変更します。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスします。  詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
## Windows アプリケーションの作成  
 最初に **Windows アプリケーション**を作成します。  この手順ではプロジェクトへの名前の割り当てはオプションですが、後でこのプロジェクトを保存するため、プロジェクトに名前を付けます。  
  
#### 新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューで新しいプロジェクトを作成します。  
  
2.  プロジェクトに `UpdateMultipleTablesWalkthrough` という名前を付けます。  
  
3.  **\[Windows アプリケーション\]** をクリックし、**\[OK\]** をクリックします。  詳細については、「[クライアント アプリケーション](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)」を参照してください。  
  
     **UpdateMultipleTablesWalkthrough** プロジェクトが作成されて**ソリューション エクスプローラー**に追加されます。  
  
## データ ソースの作成  
 この手順では、**データ ソース構成**ウィザードを使用して、Northwind データベースからデータ ソースを作成します。  接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。  Northwind サンプル データベースのセットアップの詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
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
  
8.  **Customers** テーブルと **Orders** テーブルを選択し、**\[完了\]** をクリックします。  
  
     プロジェクトに **NorthwindDataSet** が追加され、**\[データ ソース\]** ウィンドウにテーブルが表示されます。  
  
## 作成するコントロールの設定  
 このチュートリアルでは、データが個別のコントロールに表示される**詳細**レイアウトで、`Customers` テーブル内のデータを表示します。  `Orders` テーブルのデータは、<xref:System.Windows.Forms.DataGridView> コントロール内に表示される **グリッド** レイアウトで表示します。  
  
#### \[データ ソース\] ウィンドウの項目のドロップ タイプを設定するには  
  
1.  **\[データ ソース\]** ウィンドウの **\[Customers\]** ノードを展開します。  
  
2.  **\[Customers\]** ノードのコントロール リストの **\[詳細\]** を選択し、**Customers** テーブルのコントロールを個別のコントロールに変更します。  詳細については、「[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)」を参照してください。  
  
## データ バインド フォームの作成  
 **\[データ ソース\]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。  
  
#### フォームにデータ バインド コントロールを作成するには  
  
1.  **\[データ ソース\]** ウィンドウから **Form1** にメインの **\[Customers\]** ノードをドラッグします。  
  
     説明のラベルが付いたデータ バインド コントロールとレコード間を移動するためのツール ストリップ \(<xref:System.Windows.Forms.BindingNavigator>\) がフォームに表示されます。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource>、および <xref:System.Windows.Forms.BindingNavigator> がコンポーネント トレイに表示されます。  
  
2.  **\[データ ソース\]** ウィンドウから **Form1** に **\[Orders\]** ノードをドラッグします。  
  
    > [!NOTE]
    >  関連する **\[Orders\]** ノードは **\[Fax\]** 列の下にあり、**\[Customers\]** ノードの子ノードです。  
  
     レコード間をナビゲートするための <xref:System.Windows.Forms.DataGridView> コントロールとツール ストリップ \(<xref:System.Windows.Forms.BindingNavigator>\) がフォームに表示されます。  コンポーネント トレイに [OrdersTableAdapter](../data-tools/tableadapter-overview.md) と <xref:System.Windows.Forms.BindingSource> が表示されます。  
  
## データベースを更新するコードの追加  
 **Customers** TableAdapter および **Orders** TableAdapter の `Update` メソッドを呼び出して、データベースを更新できます。  既定では、<xref:System.Windows.Forms.BindingNavigator> の **\[データの保存\]** ボタンのイベント ハンドラーが、データベースへの更新を送信するフォームのコードに追加されます。  この手順では、正しい順序で更新を送信し、参照整合性エラーが発生する可能性がなくなるようにコードを変更します。  また、Update 呼び出しを try\-catch ブロックにラップして、エラー処理も実装します。  アプリケーションの要件に適合するようにコードを変更できます。  
  
> [!NOTE]
>  説明をわかりやすくするために、ここではトランザクションを使用していませんが、関連する複数のテーブルを更新する場合は、すべての更新ロジックを 1 つのトランザクションに含める必要があります。  トランザクションは、データベースに対するすべての関連する変更が正常に完了した後に、変更をコミットするプロセスです。  詳細については、「[トランザクションと同時実行](../Topic/Transactions%20and%20Concurrency.md)」を参照してください。  
  
#### アプリケーションに更新ロジックを追加するには  
  
1.  <xref:System.Windows.Forms.BindingNavigator> の **\[データの保存\]** ボタンをダブルクリックして、コード エディターで `bindingNavigatorSaveItem_Click` イベント ハンドラーを開きます。  
  
2.  イベント ハンドラーのコードを、関連する TableAdapter の `Update` メソッドを呼び出すコードに置き換えます。  次のコードは、最初に、各 <xref:System.Data.DataRowState> \(<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState>、および <xref:System.Data.DataRowState>\) の更新済み情報を保持する 3 つの一時的なデータ テーブルを作成します。  次に、正しい順序で更新を実行します。  コードは、次のようになります。  
  
     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-cs[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]  
  
## アプリケーションのテスト  
  
#### アプリケーションをテストするには  
  
1.  F5 キーを押します。  
  
2.  各テーブルの 1 つ以上のレコードのデータを変更します。  
  
3.  **\[データの保存\]** をクリックします。  
  
4.  データベースの値をチェックし、変更が保存されたことを確認します。  
  
## 次の手順  
 Windows アプリケーションにデータ バインド フォームを作成した後で、アプリケーションの要件によってはさらに操作を追加する必要があります。  このチュートリアルで行うことができる拡張には次のものがあります。  
  
-   フォームに検索機能を追加します。  詳細については、「[方法: パラメーター クエリを Windows フォーム アプリケーションに追加する](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)」を参照してください。  
  
-   データ ソースを編集し、データベース オブジェクトの追加または削除を行います。  詳細については、「[方法 : データセットを編集する](../Topic/How%20to:%20Edit%20a%20Dataset.md)」を参照してください。  
  
## 参照  
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)