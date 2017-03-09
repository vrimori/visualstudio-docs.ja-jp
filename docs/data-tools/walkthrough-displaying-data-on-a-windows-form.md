---
title: "チュートリアル: Windows フォームでのデータの表示 | Microsoft Docs"
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
  - "データ [Visual Studio], 表示 (Windows フォームに)"
  - "データ バインド, Windows フォーム"
  - "表示 (データをフォームに), チュートリアル"
  - "フォーム, 表示 (データを)"
  - "Windows アプリケーション, 表示 (データを)"
  - "Windows フォーム, 表示 (データを)"
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# チュートリアル: Windows フォームでのデータの表示
アプリケーション開発で最も一般的なシナリオの 1 つは、Windows ベースのアプリケーションのフォームにデータを表示することです。  フォームにデータを表示するには、[ウィンドウ](../Topic/Data%20Sources%20Window.md)からフォームに項目をドラッグします。  このチュートリアルでは、単一のテーブルのデータを、複数の各コントロールに表示する簡単なフォームを作成します。  この例では、Northwind サンプル データベースの `Customers` テーブルを使用します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   新しい **Windows アプリケーション** プロジェクトを作成します。  
  
-   [データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を使用して、データセットを作成して構成します。  
  
-   **\[データ ソース\]** ウィンドウから項目をドラッグしたときにフォーム上に作成するコントロールを選択します。  詳細については、「[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)」を参照してください。  
  
-   **\[データ ソース\]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスします。  詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
## Windows アプリケーションの作成  
 最初に **Windows アプリケーション** プロジェクトを作成します。  
  
#### 新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューで新しいプロジェクトを作成します。  
  
2.  プロジェクトに「`DisplayingDataonaWindowsForm`」という名前を付けます。  
  
3.  **\[Windows アプリケーション\]** をクリックし、**\[OK\]** をクリックします。  詳細については、「[クライアント アプリケーション](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)」を参照してください。  
  
     **DisplayingDataonaWindowsForm** プロジェクトが作成され、**ソリューション エクスプローラー**に追加されます。  
  
## データ ソースの作成  
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
  
## 作成するコントロールの設定  
 このチュートリアルでは、**\[詳細\]** レイアウトの各コントロールにデータを表示します   \(代わりに、既定の **\[グリッド\]** レイアウトの <xref:System.Windows.Forms.DataGridView> コントロールにデータを表示することもできます\)。  
  
#### \[データ ソース\] ウィンドウの項目にドロップ タイプを設定するには  
  
1.  **\[データ ソース\]** ウィンドウの **\[Customers\]** ノードを展開します。  
  
2.  **\[Customers\]** ノードのドロップダウン リストの **\[詳細\]** をクリックして、**Customers** テーブルのドロップ タイプを **\[詳細\]** に変更します。  詳細については、「[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)」を参照してください。  
  
3.  **\[CustomerID\]** ノードのコントロール リストの **\[Label\]** をクリックして、**CustomerID** 列のドロップ タイプをラベルに変更します。  
  
## フォームの作成  
 **\[データ ソース\]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。  
  
#### フォームにデータ バインド コントロールを作成するには  
  
-   **\[データ ソース\]** ウィンドウからフォームにメインの **\[Customers\]** ノードをドラッグします。  
  
     説明のラベルが付いたデータ バインド コントロールとレコード間を移動するためのツール ストリップ \(<xref:System.Windows.Forms.BindingNavigator>\) がフォームに表示されます。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource>、および <xref:System.Windows.Forms.BindingNavigator> がコンポーネント トレイに表示されます。  
  
## アプリケーションのテスト  
  
#### アプリケーションを実行するには  
  
-   F5 キーを押します。  
  
-   <xref:System.Windows.Forms.BindingNavigator> コントロールを使用してレコード間を移動します。  
  
## 次の手順  
 アプリケーションの要件に応じて、データをバインドした Windows フォームの作成後に、追加の操作を実行できます。  このチュートリアルで行うことができる拡張には次のものがあります。  
  
-   フォームに検索機能を追加します。  詳細については、「[方法: パラメーター クエリを Windows フォーム アプリケーションに追加する](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)」を参照してください。  
  
-   データベースに更新を送信する機能を追加できます。  詳細については、「[チュートリアル : データベースへのデータの保存 \(単一テーブル\)](../Topic/Walkthrough:%20Saving%20Data%20to%20a%20Database%20\(Single%20Table\).md)」を参照してください。  
  
-   **\[データ ソース\]** ウィンドウの **\[ウィザードで DataSet を構成\]** をクリックして、`Orders` テーブルをデータセットに追加します。  次に、**\[Orders\]** ノード \(**Customers** テーブルの **Fax** 列の下にある\) をフォームにドラッグして、関連するデータを表示するコントロールを追加できます。  詳細については、「[方法: 関連するデータを Windows フォーム アプリケーションに表示する](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)」を参照してください。  
  
## 参照  
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)   
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)