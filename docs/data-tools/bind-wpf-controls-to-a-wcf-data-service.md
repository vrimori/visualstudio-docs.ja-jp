---
title: "チュートリアル: WCF Data Service への WPF コントロールのバインド | Microsoft Docs"
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
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 40
caps.handback.revision: 38
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# チュートリアル: WCF Data Service への WPF コントロールのバインド
このチュートリアルでは、データ バインド コントロールが含まれた WPF アプリケーションを作成します。  コントロールは、[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] でカプセル化された顧客レコードにバインドされます。  また、顧客がレコードを表示および更新するために使用できるボタンも追加します。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   AdventureWorksLT サンプル データベースのデータから生成される Entity Data Model を作成する。  
  
-   WPF アプリケーションに Entity Data Model のデータを公開する [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] を作成する。  
  
-   **\[データ ソース\]** ウィンドウから WPF デザイナーに項目をドラッグして、一連のデータ バインド コントロールを作成する。  
  
-   顧客レコード間を前後に移動するためのボタンを作成する。  
  
-   コントロールでのデータに対する変更を [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] および基になるデータ ソースに保存するボタンを作成する。  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   AdventureWorksLT サンプル データベースが添付された、SQL Server または SQL Server Express の実行中のインスタンスへのアクセス権。  AdventureWorksLT データベースは [CodePlex Web サイト](http://go.microsoft.com/fwlink/?linkid=87843)からダウンロードできます。  
  
 次の概念に関する知識があると役立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   WCF Data Services。  詳細については、「[概要](../Topic/WCF%20Data%20Services%20Overview.md)」を参照してください。  
  
-   [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] のデータ モデル。  
  
-   Entity Data Model および ADO.NET Entity Framework。  詳細については、「[エンティティ フレームワークの概要](../Topic/Entity%20Framework%20Overview.md)」を参照してください。  
  
-   WPF デザイナーの操作。  詳細については、「[WPF および Silverlight デザイナーの概要](http://msdn.microsoft.com/ja-jp/570b7a5c-0c86-4326-a371-c9b63378fc62)」を参照してください。  
  
-   WPF データ バインディング。  詳細については、「[データ バインドの概要](../Topic/Data%20Binding%20Overview.md)」を参照してください。  
  
## サービス プロジェクトの作成  
 このチュートリアルでは、まず [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] のプロジェクトを作成します。  
  
#### サービス プロジェクトを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
3.  **\[Visual C\#\]** または **\[Visual Basic\]** を展開し、**\[Web\]** を選択します。  
  
4.  **\[ASP.NET Web アプリケーション\]** プロジェクト テンプレートを選択します。  
  
5.  **\[プロジェクト名\]** ボックスに「`AdventureWorksService`」と入力し、**\[OK\]** をクリックします。  
  
     Visual Studio によって `AdventureWorksService` プロジェクトが作成されます。  
  
6.  **ソリューション エクスプローラー**で、**Default.aspx** を右クリックし、**\[削除\]** を選択します。  このファイルは、このチュートリアルでは必要ありません。  
  
## サービスの Entity Data Model の作成  
 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] を使用してアプリケーションにデータを公開するには、サービスのデータ モデルを定義する必要があります。  [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] は、Entity Data Model とカスタム データ モデルの 2 種類のデータ モデルをサポートしています。これらは、<xref:System.Linq.IQueryable%601> インターフェイスを実装する共通言語ランタイム \(CLR: Common Language Runtime\) オブジェクトを使用して定義されます。  このチュートリアルでは、データ モデルとして Entity Data Model を作成します。  
  
#### Entity Data Model を作成するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  \[インストールされたテンプレート\] ボックスの一覧で、**\[データ\]** をクリックし、**\[ADO.NET エンティティ データ モデル\]** プロジェクト項目を選択します。  
  
3.  名前を「`AdventureWorksModel.edmx`」に変更し、**\[追加\]** をクリックします。  
  
     **Entity Data Model ウィザード**が開きます。  
  
4.  **\[モデルのコンテンツの選択\]** ページで、**\[データベースから生成\]** をクリックし、**\[次へ\]** をクリックします。  
  
5.  **\[データ接続の選択\]** ページで、次のいずれかのオプションを選択します。  
  
    -   AdventureWorksLT サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は、これを選択します。  
  
         または  
  
    -   **\[新しい接続\]** をクリックして、AdventureWorksLT データベースへの接続を作成します。  
  
6.  **\[データ接続の選択\]** ページで、**\[エンティティ接続設定に名前を付けて App.Config に保存\]** オプションが選択されていることを確認し、**\[次へ\]** をクリックします。  
  
7.  **\[データベース オブジェクトの選択\]** ページで、**\[テーブル\]** を展開し、**SalesOrderHeader** テーブルを選択します。  
  
8.  **\[完了\]** をクリックします。  
  
## サービスの作成  
 WPF アプリケーションに Entity Data Model のデータを公開する [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] を作成します。  
  
#### サービスを作成するには  
  
1.  **\[プロジェクト\]** メニューで **\[新しい項目の追加\]** を選択します。  
  
2.  \[インストールされたテンプレート\] ボックスの一覧で、で、**\[Web\]** をクリックし、**\[WCF Data Service\]** プロジェクト項目を選択します。  
  
3.  **\[プロジェクト名\]** ボックスに、「`AdventureWorksService.svc`」と入力し、**\[追加\]** をクリックします。  
  
     Visual Studio によってプロジェクトに `AdventureWorksService.svc` が追加されます。  
  
## サービスの構成  
 作成した Entity Data Model を操作するには、サービスを構成する必要があります。  
  
#### サービスを構成するには  
  
1.  `AdventureWorks.svc` コード ファイルで、`AdventureWorksService` クラス宣言を次のコードで置き換えます。  
  
     [!code-cs[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]  
  
     このコードにより `AdventureWorksService` クラスが更新され、Entity Data Model の `AdventureWorksLTEntities` オブジェクト コンテキスト クラスを操作する <xref:System.Data.Services.DataService%601> の派生クラスになります。  また、`InitializeService` メソッドも更新され、`SalesOrderHeader` エンティティへの完全な読み取り\/書き込みアクセスがサービスのクライアントに許可されます。  
  
2.  プロジェクトをビルドし、エラーが発生しないことを確認します。  
  
## WPF クライアント アプリケーションの作成  
 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] のデータを表示するには、サービスに基づくデータ ソースを使用して、新しい WPF アプリケーションを作成します。  このチュートリアルの後半で、データ バインド コントロールをアプリケーションに追加します。  
  
#### WPF クライアント アプリケーションを作成するには  
  
1.  **ソリューション エクスプローラー**で、ソリューション ノードを右クリックし、**\[追加\]** をクリックして、**\[新しいプロジェクト\]** を選択します。  
  
2.  **\[新しいプロジェクト\]** ダイアログで、**\[Visual C\#\]** または **\[Visual Basic\]** を展開し、**\[Windows\]** を選択します。  
  
3.  **\[WPF アプリケーション\]** プロジェクト テンプレートを選択します。  
  
4.  **\[プロジェクト名\]** ボックスに「`AdventureWorksSalesEditor`」と入力し、**\[OK\]** をクリックします。  
  
     Visual Studio によってソリューションに `AdventureWorksSalesEditor` プロジェクトが追加されます。  
  
5.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  
  
     **\[データ ソース\]** ウィンドウが開きます。  
  
6.  **\[データ ソース\]** ウィンドウで、**\[新しいデータ ソースの追加\]** をクリックします。  
  
     **データ ソース構成**ウィザードが開きます。  
  
7.  ウィザードの **\[データ ソースの種類を選択\]** ページで、**\[サービス\]** を選択し、**\[次へ\]** をクリックします。  
  
8.  **\[サービス参照の追加\]** ダイアログ ボックスで **\[探索\]** をクリックします。  
  
     Visual Studio によって、使用できるサービスが現在のソリューションから検索され、**\[サービス\]** ボックスの使用できるサービスの一覧に `AdventureWorksService.svc` が追加されます。  
  
9. **\[名前空間\]** ボックスに「`AdventureWorksService`」と入力します。  
  
10. **\[サービス\]** ボックスで **\[AdventureWorksService.svc\]** をクリックし、**\[OK\]** をクリックします。  
  
     Visual Studio によってサービス情報がダウンロードされ、**データ ソース構成ウィザード**に戻ります。  
  
11. **\[サービス参照の追加\]** ページで、**\[完了\]** をクリックします。  
  
     Visual Studio によって、サービスから返されたデータを表すノードが **\[データ ソース\]** ウィンドウに追加されます。  
  
## ウィンドウのユーザー インターフェイスの定義  
 WPF デザイナーで XAML を変更して、いくつかのボタンをウィンドウに追加します。  これらのボタンを使用して販売レコードを表示および更新できるようにするコードは、このチュートリアルで後で追加します。  
  
#### ウィンドウ レイアウトを作成するには  
  
1.  **ソリューション エクスプローラー**で、MainWindow.xaml をダブルクリックします。  
  
     WPF デザイナーでウィンドウが開きます。  
  
2.  デザイナーの [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] ビューで、`<Grid>` タグの間に次のコードを追加します。  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="525" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  プロジェクトをビルドします。  
  
## データ バインド コントロールの作成  
 顧客レコードを表示するコントロールを作成するには、**\[データ ソース\]** ウィンドウからデザイナーに `[SalesOrderHeaders]` ノードをドラッグします。  
  
#### データ バインディング コントロールを作成するには  
  
1.  **\[データ ソース\]** ウィンドウで、**\[SalesOrderHeaders\]** ノードのドロップダウン メニューをクリックし、**\[詳細\]** を選択します。  
  
2.  **\[SalesOrderHeaders\]** ノードを展開します。  
  
3.  この例ではいくつかのフィールドを非表示にするために、次のノードの横のドロップダウン メニューをクリックして **\[なし\]** を選択します。  
  
    -   **CreditCardApprovalCode**  
  
    -   **ModifiedDate**  
  
    -   **OnlineOrderFlag**  
  
    -   **RevisionNumber**  
  
    -   **rowguid**  
  
     この操作は、次の手順において、これらのノードに対応するデータ バインド コントロールが Visual Studio で作成されるのを防ぎます。  このチュートリアルでは、これらのデータをエンド ユーザーが参照する必要はありません。  
  
4.  **\[データ ソース\]** ウィンドウから、ボタンのある行の下のグリッド行に **\[SalesOrderHeaders\]** ノードをドラッグします。  
  
     Visual Studio によって、**Product** テーブルのデータにバインドされるコントロール セットを作成する XAML とコードが生成されます。  生成される XAML およびコードの詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
5.  デザイナーで、**\[Customer ID\]** ラベルの横のテキスト ボックスをクリックします。  
  
6.  **\[プロパティ\]** ウィンドウで、**IsReadOnly** プロパティの横のチェック ボックスをオンにします。  
  
7.  次の各テキスト ボックスに **IsReadOnly** プロパティを設定します。  
  
    -   **\[Purchase Order Number\]**  
  
    -   **\[Sales Order ID\]**  
  
    -   **\[Sales Order Number\]**  
  
## サービスからのデータの読み込み  
 サービスから販売データを読み込むには、サービス プロキシ オブジェクトを使用します。その後、返されたデータを、WPF ウィンドウの <xref:System.Windows.Data.CollectionViewSource> のデータ ソースに割り当てます。  
  
#### サービスからデータを読み込むには  
  
1.  デザイナーで、**MainWindow** というテキストをダブルクリックして、`Window_Loaded` イベント ハンドラーを作成します。  
  
2.  イベント ハンドラーを次のコードで置き換えます。  このコードの *localhost* アドレスは、使用している開発コンピューターのローカル ホスト アドレスで置き換えてください。  
  
     [!code-cs[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]  
  
## 販売レコード間の移動  
 ユーザーが **\[\<\]** ボタンと **\[\>\]** ボタンを使用して販売レコード間をスクロールできるようにするコードを追加します。  
  
#### ユーザーが販売レコード間を移動できるようにするには  
  
1.  デザイナーで、ウィンドウ サーフェイスの **\[\<\]** をダブルクリックします。  
  
     Visual Studio によって分離コード ファイルが開かれ、<xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントのために、新しい `backButton_Click` イベント ハンドラーが作成されます。  
  
2.  生成された `backButton_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-cs[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]  
  
3.  デザイナーに戻り、**\[\>\]** をダブルクリックします。  
  
     Visual Studio によって分離コード ファイルが開かれ、<xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントのために、新しい `nextButton_Click` イベント ハンドラーが作成されます。  
  
4.  生成された `nextButton_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-cs[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]  
  
## 販売レコードへの変更の保存  
 ユーザーが販売レコードを表示し、**\[変更の保存\]** ボタンを使用して変更を保存できるようにするコードを追加します。  
  
#### 販売レコードへの変更を保存する機能を追加するには  
  
1.  デザイナーで、**\[変更の保存\]** をダブルクリックします。  
  
     Visual Studio によって分離コード ファイルが開かれ、<xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントのために、新しい `saveButton_Click` イベント ハンドラーが作成されます。  
  
2.  `saveButton_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-cs[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]  
  
## アプリケーションのテスト  
 アプリケーションをビルドして実行し、顧客レコードを表示および更新できることを確認します。  
  
#### アプリケーションをテストするには  
  
1.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  ソリューションがエラーなしでビルドされることを確認します。  
  
2.  **Ctrl キーを押しながら F5 キー**を押します。  
  
     Visual Studio によって、**AdventureWorksService** プロジェクトがデバッグなしで開始されます。  
  
3.  **ソリューション エクスプローラー**で、**AdventureWorksSalesEditor** プロジェクトを右クリックします。  
  
4.  コンテキスト メニューの **\[デバッグ\]** で、**\[新しいインスタンスを開始\]** をクリックします。  
  
     アプリケーションが実行されます。  次のことを検証します。  
  
    -   テキスト ボックスに、先頭の販売レコードの各種データ フィールドが表示されること。このレコードの販売注文 ID は **71774** です。  
  
    -   **\[\>\]** または **\[\<\]** をクリックして、他の販売レコードに移動できること。  
  
5.  いずれかの販売レコードの **\[コメント\]** ボックスに任意のテキストを入力し、**\[変更の保存\]** をクリックします。  
  
6.  アプリケーションを終了し、Visual Studio からもう一度アプリケーションを起動します。  
  
7.  変更した販売レコードに移動し、アプリケーションを終了して再起動した後でも変更が保持されていることを確認します。  
  
8.  アプリケーションを終了します。  
  
## 次の手順  
 このチュートリアルを完了した後、関連する次のタスクを実行できます。  
  
-   Visual Studio の **\[データ ソース\]** ウィンドウを使用して、WPF コントロールをその他の種類のデータ ソースにバインドする方法について学習します。  詳細については、「[チュートリアル: データセットへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-dataset.md)」を参照してください。  
  
-   Visual Studio の **\[データ ソース\]** ウィンドウを使用して、WPF コントロールでの関連するデータ \(つまり、親子関係にあるデータ\) を表示する方法について学習します。  詳細については、「[チュートリアル: WPF アプリケーションでの関連データの表示](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)」を参照してください。  
  
## 参照  
 [Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [方法: Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [チュートリアル: データセットへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [概要](../Topic/WCF%20Data%20Services%20Overview.md)   
 [エンティティ フレームワークの概要](../Topic/Entity%20Framework%20Overview.md)   
 [WPF および Silverlight デザイナーの概要](http://msdn.microsoft.com/ja-jp/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [データ バインドの概要](../Topic/Data%20Binding%20Overview.md)