---
title: "チュートリアル: WPF アプリケーションでの関連データの表示 | Microsoft Docs"
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
  - "WPF データ バインド [Visual Studio], チュートリアル"
  - "WPF デザイナー, データ バインド"
  - "WPF, データ バインド (Visual Studio での)"
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# チュートリアル: WPF アプリケーションでの関連データの表示
このチュートリアルでは、親子のリレーションシップを持つデータベース テーブルのデータを表示する WPF アプリケーションを作成します。  データは、Entity Data Model のエンティティにカプセル化されます。  親エンティティには、一連の注文についての概要情報が含まれます。  このエンティティの各プロパティは、アプリケーション内の別々のコントロールにバインドされます。  子エンティティには、各注文の詳細が含まれます。  このデータ セットは、<xref:System.Windows.Controls.DataGrid> コントロールにバインドされます。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   WPF アプリケーションと、AdventureWorksLT サンプル データベースのデータから生成される Entity Data Model を作成する。  
  
-   一連の注文についての概要情報を表示するデータ バインド コントロール セットを作成する。  **\[データ ソース\]** ウィンドウから **WPF デザイナー**に親エンティティをドラッグして、コントロールを作成します。  
  
-   選択した注文ごとに関連する詳細情報を表示する <xref:System.Windows.Controls.DataGrid> コントロールを作成する。  **\[データ ソース\]** ウィンドウから **WPF デザイナー**内のウィンドウに子エンティティをドラッグして、コントロールを作成します。  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   AdventureWorksLT サンプル データベースがアタッチされた、SQL Server または SQL Server Express の実行中のインスタンスへのアクセス。  AdventureWorksLT データベースは、[CodePlex の Web サイト](http://go.microsoft.com/fwlink/?linkid=87843)からダウンロードできます。  
  
 次の概念に関する予備知識があると役に立ちますが、チュートリアルを完了するうえで必須ではありません。  
  
-   エンティティ データ モデルおよび ADO.NET Entity Framework。  詳細については、「[エンティティ フレームワークの概要](../Topic/Entity%20Framework%20Overview.md)」を参照してください。  
  
-   WPF デザイナーの操作。  詳細については、「[WPF および Silverlight デザイナーの概要](http://msdn.microsoft.com/ja-jp/570b7a5c-0c86-4326-a371-c9b63378fc62)」を参照してください。  
  
-   WPF のデータ バインディング。  詳細については、「[データ バインドの概要](../Topic/Data%20Binding%20Overview.md)」を参照してください。  
  
## プロジェクトの作成  
 注文レコードを表示するには、新しい WPF プロジェクトを作成します。  
  
#### 新しい WPF プロジェクトを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
3.  **\[Visual C\#\]** または **\[Visual Basic\]** を展開し、**\[Windows\]** を選択します。  
  
4.  ダイアログ ボックスの上部のコンボ ボックスで、**\[.NET Framework 4\]** が選択されていることを確認します。  このチュートリアルで使用する <xref:System.Windows.Controls.DataGrid> コントロールは、.NET Framework 4 でのみ使用できます。  
  
5.  **\[WPF アプリケーション\]** プロジェクト テンプレートを選択します。  
  
6.  **\[プロジェクト名\]** ボックスに「`AdventureWorksOrdersViewer`」と入力します。  
  
7.  **\[OK\]** をクリックします。  
  
     Visual Studio によって、`AdventureWorksOrdersViewer` プロジェクトが作成されます。  
  
## アプリケーションで使用する Entity Data Model の作成  
 データ バインド コントロールを作成するには、アプリケーションで使用するデータ モデルを定義し、**\[データ ソース\]** ウィンドウに追加する必要があります。  このチュートリアルで使用するデータ モデルは Entity Data Model です。  
  
#### Entity Data Model を作成するには  
  
1.  **\[データ\]** メニューで、**\[新しいデータ ソースの追加\]** をクリックし、**データ ソース構成**ウィザードを起動します。  
  
2.  **\[データソースの種類を選択\]** ページで、**\[データベース\]** を選択し、**\[次へ\]** をクリックします。  
  
3.  **\[データベース モデルの選択\]** ページで、**\[Entity Data Model\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  **\[モデルのコンテンツの選択\]** ページで、**\[データベースから生成\]** をクリックし、**\[次へ\]** をクリックします。  
  
5.  **\[データ接続の選択\]** ページで、次のいずれかの操作を実行します。  
  
    -   AdventureWorksLT サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は、それを選択します。  
  
         または  
  
    -   **\[新しい接続\]** をクリックし、AdventureWorksLT データベースへの接続を作成します。  
  
     **\[エンティティ接続設定に名前を付けて App.Config に保存\]** オプションが選択されていることを確認し、**\[次へ\]** をクリックします。  
  
6.  **\[データベース オブジェクトの選択\]** ページで、**\[テーブル\]** を展開し、次のテーブルを選択します。  
  
    -   **SalesOrderDetail**  
  
    -   **SalesOrderHeader**  
  
7.  \[完了\] をクリックします。  
  
8.  プロジェクトをビルドします。  
  
## 注文を表示するデータ バインド コントロールの作成  
 注文レコードを表示するコントロールを作成するには、**\[データ ソース\]** ウィンドウから WPF デザイナーに `SalesOrderHeaders` エンティティをドラッグします。  
  
#### 注文レコードを表示するデータ バインド コントロールを作成するには  
  
1.  **ソリューション エクスプローラー**で、MainWindow.xaml をダブルクリックします。  
  
     WPF デザイナーでウィンドウが開きます。  
  
2.  XAML を編集して、**Height** プロパティと **Width** プロパティを 800 に設定します。  
  
3.  **\[データ ソース\]** ウィンドウで、**\[SalesOrderHeaders\]** ノードのドロップダウン メニューをクリックし、**\[詳細\]** を選択します。  
  
4.  **\[SalesOrderHeaders\]** ノードを展開します。  
  
5.  **\[SalesOrderID\]** の横にあるドロップダウン メニューをクリックし、**\[ComboBox\]** を選択します。  
  
6.  **\[SalesOrderHeaders\]** ノードの次の各子ノードの横にあるドロップダウン メニューをクリックし、**\[なし\]** を選択します。  
  
    -   **RevisionNumber**  
  
    -   **OnlineOrderFlag**  
  
    -   **ShipToAddressID**  
  
    -   **BillToAddressID**  
  
    -   **CreditCardApprovalCode**  
  
    -   **SubTotal**  
  
    -   **TaxAmt**  
  
    -   **Freight**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     この操作は、次の手順において、これらのノードに対応するデータ バインド コントロールが Visual Studio で作成されるのを防ぎます。  このチュートリアルでは、これらのデータをエンド ユーザーが参照する必要はありません。  
  
7.  **\[データ ソース\]** ウィンドウから **WPF デザイナー**内のウィンドウに、**\[SalesOrderHeaders\]** ノードをドラッグします。  
  
     Visual Studio によって、**SalesOrderHeaders** エンティティのデータにバインドされるコントロール セットを作成する XAML と、データを読み込むコードが生成されます。  生成される XAML とコードの詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
8.  デザイナーで、**\[Sales Order ID\]** ラベルの横にあるコンボ ボックスをクリックします。  
  
9. **\[プロパティ\]** ウィンドウで、**IsReadOnly** プロパティの横にあるチェック ボックスをオンにします。  
  
## 注文の詳細を表示する DataGrid の作成  
 注文の詳細を表示する <xref:System.Windows.Controls.DataGrid> コントロールを作成するには、**\[データ ソース\]** ウィンドウから WPF デザイナーに `SalesOrderDetails` エンティティをドラッグします。  
  
#### 注文の詳細を表示する DataGrid を作成するには  
  
1.  **\[データ ソース\]** ウィンドウで、**\[SalesOrderHeaders\]** ノードの子である **\[SalesOrderDetails\]** ノードを検索します。  
  
    > [!NOTE]
    >  **\[SalesOrderDetails\]** ノードの中には、**\[SalesOrderHeaders\]** ノードのピアであるものもあります。  必ず **\[SalesOrderHeaders\]** ノードの子ノードを選択するようにしてください。  
  
2.  子の **\[SalesOrderDetails\]** ノードを展開します。  
  
3.  **\[SalesOrderDetails\]** ノードの次の各子ノードの横にあるドロップダウン メニューをクリックし、**\[なし\]** を選択します。  
  
    -   **SalesOrderID**  
  
    -   **SalesOrderDetailID**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     この操作は、次の手順において、このデータが Visual Studio によって <xref:System.Windows.Controls.DataGrid> コントロールに追加されるのを防ぎます。  このチュートリアルでは、これらのデータをエンド ユーザーが参照する必要はありません。  
  
4.  **\[データ ソース\]** ウィンドウから **WPF デザイナー**内のウィンドウに、子の **\[SalesOrderDetails\]** ノードをドラッグします。  
  
     Visual Studio によって、新しいデータ バインド <xref:System.Windows.Controls.DataGrid> コントロールを定義する XAML が生成され、デザイナー内にコントロールが表示されます。  また、分離コード ファイル内に生成された `GetSalesOrderHeadersQuery` メソッドも、**SalesOrderDetails** エンティティのデータを含めるように更新されます。  
  
## アプリケーションのテスト  
 アプリケーションをビルドして実行し、注文レコードが表示されることを確認します。  
  
#### アプリケーションをテストするには  
  
1.  **F5** キーを押します。  
  
     アプリケーションがビルドされ、実行されます。  次の点を確認します。  
  
    -   **\[Sales Order ID\]** コンボ ボックスに **"71774"** と表示されます。  これはエンティティの最初の注文 ID です。  
  
    -   **\[Sales Order ID\]** ボックスの一覧で選択した注文ごとに、詳細な注文情報が <xref:System.Windows.Controls.DataGrid> に表示されること。  
  
2.  アプリケーションを閉じます。  
  
## 次の手順  
 このチュートリアルを完了したら、Visual Studio で **\[データ ソース\]** ウィンドウを使用して、WPF コントロールを他の種類のデータ ソースにバインドする方法を学習できます。  詳細については、「[チュートリアル: WCF Data Service への WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)」および「[チュートリアル: データセットへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-dataset.md)」を参照してください。  
  
## 参照  
 [Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [方法: WPF アプリケーションで関連データを表示する](../data-tools/display-related-data-in-wpf-applications.md)