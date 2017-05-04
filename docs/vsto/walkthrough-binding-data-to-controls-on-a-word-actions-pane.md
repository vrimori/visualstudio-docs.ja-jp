---
title: "チュートリアル : Word の操作ウィンドウ上のコントロールへのデータ バインド | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "操作ウィンドウ [Visual Studio での Office 開発], バインド (コントロールを)"
  - "操作ウィンドウ [Visual Studio での Office 開発], データ バインド"
  - "コントロール [Visual Studio での Office 開発], データ バインド"
  - "データ バインド [Visual Studio での Office 開発], 操作ウィンドウ"
  - "データ バインド [Visual Studio での Office 開発], スマート ドキュメント"
  - "スマート ドキュメント [Visual Studio での Office 開発], データ バインド"
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: 64
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# チュートリアル : Word の操作ウィンドウ上のコントロールへのデータ バインド
  このチュートリアルでは、Word の操作ウィンドウ内のコントロールにデータ バインディングを示します。  このコントロールは、SQL Server データベースのテーブル間のマスター\/詳細リレーションシップを示します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   データにバインドされた Windows フォーム コントロールを含む操作ウィンドウを作成します。  
  
-   マスター\/詳細リレーションシップを使用してコントロール内にデータを表示します。  
  
-   アプリケーションが開かれたときに操作ウィンドウを表示します。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
-   Northwind SQL Server サンプル データベースがインストールされたサーバーへのアクセス  
  
-   SQL Server データベースの読み込み\/書き込みアクセス許可  
  
## プロジェクトの作成  
 まず、Word 文書プロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  My Word Actions Pane という名前の Word 文書プロジェクトを作成します。  ウィザードで、**\[新規ドキュメントの作成\]** をクリックします。  
  
     詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     新しい Word 文書が Visual Studio のデザイナーに開かれ、**My Word Actions Pane** プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## 操作ウィンドウへのコントロールの追加  
 このチュートリアルでは、データ バインド Windows フォーム コントロールがある操作ウィンドウ コントロールが必要です。  データ ソースをプロジェクトに追加し、**\[データ ソース\]** ウィンドウからコントロールを操作ウィンドウ コントロールにドラッグします。  
  
#### 操作ウィンドウ コントロールを追加するには  
  
1.  **ソリューション エクスプローラー**の **\[My Word Actions Pane\]** プロジェクトを選択します。  
  
2.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
3.  **\[新しい項目の追加\]** ダイアログ ボックスの **\[操作ウィンドウ コントロール\]** をクリックし、コントロールに **ActionsControl** という名前を付けて **\[追加\]** をクリックします。  
  
#### プロジェクトにデータ ソースを追加するには  
  
1.  **\[データ ソース\]** のウィンドウが表示されない場合は、これを、**\[ビュー\]**、**\[その他のウィンドウ\]** を選択する、メニュー バーの **\[データ ソース\]** 表示されます。  
  
    > [!NOTE]  
    >  **\[データ ソースの表示\]** が使用できない場合は、Word 文書をクリックしてから、再び確認してください。  
  
2.  **\[新しいデータ ソースの追加\]** をクリックして**データ ソース構成**ウィザードを起動します。  
  
3.  **\[データベース\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  SQL Server Northwind サンプル データベースへのデータ接続を選択するか、または **\[新しい接続\]** をクリックして新しい接続を追加します。  
  
5.  **\[次へ\]** をクリックします。  
  
6.  接続を保存するオプションがオンになっている場合はオフにし、**\[次へ\]** をクリックします。  
  
7.  **\[データベース オブジェクト\]** ウィンドウの **\[テーブル\]** ノードを展開します。  
  
8.  **\[Suppliers\]** テーブルと **\[Products\]** テーブルの横にあるチェック ボックスをオンにします。  
  
9. \[完了\] をクリックします。  
  
 **\[Suppliers\]** テーブルと **\[Products\]** テーブルが **\[データ ソース\]** ウィンドウに追加されます。  さらに、**ソリューション エクスプローラー**に表示されるプロジェクトに、型指定されたデータセットも追加されます。  
  
#### データ バインド Windows フォーム コントロールを操作ウィンドウ コントロールに追加するには  
  
1.  **\[データ ソース\]** ウィンドウの **\[Suppliers\]** テーブルを展開します。  
  
2.  **\[会社名\]** ノードのドロップダウン矢印をクリックし、**\[ComboBox\]** をクリックします。  
  
3.  **\[データ ソース\]** ウィンドウの **\[CompanyName\]** を操作ウィンドウ コントロールにドラッグします。  
  
     <xref:System.Windows.Forms.ComboBox> コントロールが、操作ウィンドウ コントロールに作成されます。  さらに、`SuppliersBindingSource` という <xref:System.Windows.Forms.BindingSource>、テーブル アダプター、および <xref:System.Data.DataSet> がプロジェクトのコンポーネント トレイに追加されます。  
  
4.  **\[コンポーネント\]** トレイの `SuppliersBindingNavigator` を選択し、Del キーを押します。  このチュートリアルでは `SuppliersBindingNavigator` は使用しません。  
  
    > [!NOTE]  
    >  `SuppliersBindingNavigator` を削除しても、それのために作成されたすべてのコードは削除されません。  このコードは削除できます。  
  
5.  コンボ ボックスをラベルの下へ移動して、**\[Size\]** プロパティを 171, 21 に変更します。  
  
6.  **\[データ ソース\]** ウィンドウで、**\[Suppliers\]** テーブルの子である **\[Products\]** テーブルを展開します。  
  
7.  **\[ProductName\]** ノードのドロップダウン矢印をクリックし、**\[ListBox\]** をクリックします。  
  
8.  **\[ProductName\]** を操作ウィンドウ コントロールにドラッグします。  
  
     <xref:System.Windows.Forms.ListBox> コントロールが、操作ウィンドウ コントロールに作成されます。  それと同時に、`ProductBindingSource` という <xref:System.Windows.Forms.BindingSource> とテーブル アダプターがプロジェクトのコンポーネント トレイに追加されます。  
  
9. リスト ボックスをラベルの下へ移動して、**\[Size\]** プロパティを 171, 95 に変更します。  
  
10. **ツールボックス**から <xref:System.Windows.Forms.Button> を操作ウィンドウ コントロールにドラッグし、リスト ボックスの下に配置します。  
  
11. <xref:System.Windows.Forms.Button> を右クリックし、ショートカット メニューの **\[プロパティ\]** をクリックし、次のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**\[挿入\]**|  
    |**テキスト**|**\[挿入\]**|  
  
12. ユーザー コントロールのサイズをコントロールと同じ大きさに変更します。  
  
## データ ソースの設定  
 データ ソースをセットアップするには、操作ウィンドウ コントロールの <xref:System.Windows.Forms.UserControl.Load> イベントに <xref:System.Data.DataTable> からデータを取得してコントロールに読み込むコードを追加し、各コントロールに対して <xref:System.Windows.Forms.Binding.DataSource%2A> プロパティと <xref:System.Windows.Forms.BindingSource.DataMember%2A> プロパティを設定します。  
  
#### コントロールにデータを読み込むには  
  
1.  `ActionsControl` クラスの <xref:System.Windows.Forms.UserControl.Load> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#1)]  
  
2.  C\# では、イベント ハンドラーを <xref:System.Windows.Forms.UserControl.Load> イベントに追加する必要があります。  `InitializeComponent` の呼び出しの後に、このコードを `ActionsControl` コンストラクターに追加できます。  イベント ハンドラーを作成する方法の詳細については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#33)]  
  
#### コントロールのデータ バインド プロパティを設定するには  
  
1.  `CompanyNameComboBox` コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウの **DataSource** プロパティの右側にあるボタンをクリックし、**\[suppliersBindingSource\]** をクリックします。  
  
3.  **\[DisplayMember\]** プロパティの右側にあるボタンをクリックし、**\[CompanyName\]** をクリックします。  
  
4.  **\[DataBindings\]** プロパティを展開し、**\[Text\]** プロパティの右側にあるボタンをクリックして、**\[None\]** をクリックします。  
  
5.  `ProductNameListBox` コントロールを選択します。  
  
6.  **\[プロパティ\]** ウィンドウの **DataSource** プロパティの右側にあるボタンをクリックし、**\[productsBindingSource\]** をクリックします。  
  
7.  **\[DisplayMember\]** プロパティの右側にあるボタンをクリックし、**\[ProductName\]** をクリックします。  
  
8.  **\[DataBindings\]** プロパティを展開し、**\[SelectedValue\]** プロパティの右側にあるボタンをクリックして、**\[None\]** をクリックします。  
  
## データをテーブルに挿入するメソッドの追加  
 次に、バインド コントロールからデータを読み取り、Word 文書内のテーブルに読み込みます。  まず、テーブルの見出しの書式を指定するためのプロシージャを作成し、次に Word テーブルを作成して書式を指定する `AddData` メソッドを追加します。  
  
#### テーブルの見出しの書式を指定するには  
  
1.  `ActionsControl` クラスに、テーブルの見出しの書式を指定するメソッドを作成します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#2)]
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#2)]  
  
#### テーブルを作成するには  
  
1.  テーブルが存在しない場合にテーブルを作成し、操作ウィンドウからデータをこのテーブルに追加するメソッドを `ActionsControl` クラスに作成します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#3)]  
  
#### Word テーブルにテキストを挿入するには  
  
1.  **\[挿入\]** ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#4)]  
  
2.  C\# では、ボタンの <xref:System.Windows.Forms.Control.Click> イベントにイベント ハンドラーを作成する必要があります。  このコードは、`ActionsControl` クラスの <xref:System.Windows.Forms.UserControl.Load> イベント ハンドラーに配置できます。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#5)]  
  
## 操作ウィンドウの表示  
 操作ウィンドウは、コントロールが追加された後で表示されます。  
  
#### 操作ウィンドウを表示するには  
  
1.  **ソリューション エクスプローラー**の **ThisDocument.vb** または **ThisDocument.cs** を右クリックし、ショートカット メニューの **\[コードの表示\]** をクリックします。  
  
2.  次のコード例に示すように、コントロールの新しいインスタンスを `ThisDocument` クラスの先頭で作成します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#6)]  
  
3.  次のコード例に示すように、`ThisDocument` の <xref:Microsoft.Office.Tools.Word.Document.Startup> イベント ハンドラーにコードを追加します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#7)]  
  
## アプリケーションのテスト  
 文書をテストして、文書を開いたときに操作ウィンドウが表示されることを確認します。  操作ウィンドウ内のコントロールのマスター\/詳細リレーションシップをテストし、**\[Insert\]** ボタンのクリック時にデータが Word 文書に読み込まれることを確認します。  
  
#### 文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  操作ウィンドウが表示されていることを確認します。  
  
3.  コンボ ボックスで会社を選択し、**\[Products\]** ボックスの一覧の内容が変更されることを確認します。  
  
4.  製品を選択し、操作ウィンドウの **\[Insert\]** をクリックして、Word 内のテーブルに製品の詳細な情報が追加されることを確認します。  
  
5.  他の製品を複数の会社から挿入します。  
  
## 次の手順  
 このチュートリアルは、Word の操作ウィンドウ内のコントロールにデータをバインドする方法の基本事項を説明します。  次に行う作業は以下のとおりです。  
  
-   Excel のコントロールへのデータのバインド。  詳細については、「[チュートリアル : Excel のアクション ペインのコントロールへのデータ連結](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)」を参照してください。  
  
-   プロジェクトの配置。  詳細については、「[ClickOnce を使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)」を参照してください。  
  
## 参照  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [方法: Word 文書または Excel ブックに操作ウィンドウを追加する](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  