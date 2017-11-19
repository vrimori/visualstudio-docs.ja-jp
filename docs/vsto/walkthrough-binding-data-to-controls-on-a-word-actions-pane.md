---
title: "チュートリアル: Word の操作ウィンドウ上のコントロールへのデータのバインド |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: "64"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a70bd325a5a9e20f9a67e59f81c63ce4b1ddcc4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-binding-data-to-controls-on-a-word-actions-pane"></a>チュートリアル : Word の操作ウィンドウ上のコントロールへのデータ バインディング
  このチュートリアルでは、Word の操作ウィンドウ上のコントロールへのデータ バインディングを示します。 このコントロールは、SQL Server データベースのテーブル間のマスター/詳細の関係を示します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   データにバインドされている Windows フォーム コントロールで、[操作] ウィンドウを作成しています。  
  
-   マスター/詳細関係を使用して、コントロールにデータを表示します。  
  
-   アプリケーションを開いたときに、[操作] ウィンドウを表示します。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
-   Northwind SQL Server サンプル データベースを持つサーバーにアクセスします。  
  
-   読み取りと書き込みの SQL Server データベースにアクセスを許可します。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初に、Word 文書のプロジェクトを作成します。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Word 文書プロジェクトを作成**My Word の操作ウィンドウ**します。 ウィザードで、次のように選択します。**新しいドキュメントを作成する**です。  
  
     詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     デザイナーで新しい Word 文書を開き、 **My Word の操作ウィンドウ**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-controls-to-the-actions-pane"></a>[操作] ウィンドウにコントロールを追加します。  
 このチュートリアルでは、操作ウィンドウ コントロールをデータ バインド Windows フォーム コントロールを含む必要があります。 プロジェクトにデータ ソースを追加し、後からコントロールをドラッグ、**データソース**操作ウィンドウ コントロールにウィンドウです。  
  
#### <a name="to-add-an-actions-pane-control"></a>操作ウィンドウ コントロールを追加するには  
  
1.  選択、 **My Word の操作ウィンドウ**プロジェクト**ソリューション エクスプ ローラー**です。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
3.  **新しい項目の追加**ダイアログ ボックスで、**操作ウィンドウ コントロール**、名前を付けます**ActionsControl**、クリックして**追加**です。  
  
#### <a name="to-add-a-data-source-to-the-project"></a>データ ソースをプロジェクトに追加するには  
  
1.  **[データ ソース]** ウィンドウが表示されていない場合は、メニュー バーの **[表示]**、 **[その他のウィンドウ]**、 **[データ ソース]**の順にクリックして表示します。  
  
    > [!NOTE]  
    >  場合**データ ソースの表示**使用できない場合、Word 文書をクリックし、もう一度確認します。  
  
2.  をクリックして**新しいデータ ソースの追加**を開始する、**データ ソース構成ウィザード**です。  
  
3.  選択**データベース** をクリックし、**次**です。  
  
4.  Northwind サンプル SQL Server データベースへのデータ接続を選択するかを使用して新しい接続を追加、**新しい接続**ボタンをクリックします。  
  
5.  **[次へ]**をクリックします。  
  
6.  クリックしてオンになっている場合、接続を保存するオプションをオフに**次**です。  
  
7.  展開して、**テーブル**内のノード、**データベース オブジェクト**ウィンドウです。  
  
8.  次のチェック ボックスをオン、 **Suppliers**と**製品**テーブル。  
  
9. **[完了]**をクリックします。  
  
 ウィザードでは追加、 **Suppliers**テーブルと**製品**テーブル、**データ ソース**ウィンドウです。 表示されているプロジェクトにも型指定されたデータセットを追加**ソリューション エクスプ ローラー**です。  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>操作ウィンドウ コントロールにデータ バインド Windows フォーム コントロールを追加するには  
  
1.  **データソース**ウィンドウで、展開、 **Suppliers**テーブル。  
  
2.  ドロップダウン矢印をクリックして、**会社名**ノード、および選択**ComboBox**です。  
  
3.  ドラッグ**CompanyName**から、**データソース**操作ウィンドウ コントロールするウィンドウです。  
  
     A<xref:System.Windows.Forms.ComboBox>操作ウィンドウ コントロールにコントロールを作成します。 同時に、<xref:System.Windows.Forms.BindingSource>という名前`SuppliersBindingSource`、テーブルのアダプターでは、および<xref:System.Data.DataSet>コンポーネント トレイにプロジェクトに追加されます。  
  
4.  選択`SuppliersBindingNavigator`で、**コンポーネント**トレイし、DEL キーを押します。 使用しない、`SuppliersBindingNavigator`このチュートリアルでします。  
  
    > [!NOTE]  
    >  削除すると、`SuppliersBindingNavigator`のすべての生成されたコードは削除されません。 このコードを削除することができます。  
  
5.  ラベルと変更されるように、コンボ ボックスを移動、**サイズ**プロパティを**171, 21**です。  
  
6.  **データ ソース**ウィンドウで、展開、**製品**の子テーブルには、 **Suppliers**テーブル。  
  
7.  ドロップダウン矢印をクリックして、 **ProductName**ノード、および選択**ListBox**です。  
  
8.  ドラッグ**ProductName**操作ウィンドウ コントロールにします。  
  
     A<xref:System.Windows.Forms.ListBox>操作ウィンドウ コントロールにコントロールを作成します。 同時に、<xref:System.Windows.Forms.BindingSource>という`ProductBindingSource`されテーブル アダプターがコンポーネント トレイに、プロジェクトに追加されます。  
  
9. ラベルと変更されるように、リスト ボックスを移動、**サイズ**プロパティを**171, 95**です。  
  
10. ドラッグ、<xref:System.Windows.Forms.Button>から、**ツールボックス**[操作] ウィンドウに制御し、リスト ボックスの下に配置します。  
  
11. 右クリックし、 <xref:System.Windows.Forms.Button>、 をクリックして**プロパティ**ショートカット メニューで、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |--------------|-----------|  
    |**名前**|**挿入します。**|  
    |**[テキスト]**|**挿入します。**|  
  
12. コントロールに合わせて、ユーザー コントロールのサイズを変更します。  
  
## <a name="setting-up-the-data-source"></a>データ ソースの設定  
 データ ソースを設定するコードを追加、<xref:System.Windows.Forms.UserControl.Load>コントロールにデータを格納から操作ウィンドウ コントロールのイベント、 <xref:System.Data.DataTable>、設定と、<xref:System.Windows.Forms.Binding.DataSource%2A>と<xref:System.Windows.Forms.BindingSource.DataMember%2A>各コントロールのプロパティです。  
  
#### <a name="to-load-the-control-with-data"></a>コントロールにデータを読み込めません  
  
1.  <xref:System.Windows.Forms.UserControl.Load>のイベント ハンドラー、`ActionsControl`クラスで、次のコードを追加します。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  C# の場合は、イベント ハンドラーをアタッチする必要があります、<xref:System.Windows.Forms.UserControl.Load>イベント。 このコードを配置することができます、`ActionsControl`コンス トラクターの呼び出しの後に、`InitializeComponent`です。 イベント ハンドラーを作成する方法の詳細については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
#### <a name="to-set-data-binding-properties-of-the-controls"></a>コントロールのデータ バインディング プロパティを設定するには  
  
1.  `CompanyNameComboBox` コントロールを選択します。  
  
2.  **プロパティ** ウィンドウの右側にあるボタンをクリックして、**データソース**プロパティ、および選択**場合**です。  
  
3.  右側にあるボタンをクリックして、 **DisplayMember**プロパティ、および選択**CompanyName**です。  
  
4.  展開、 **DataBindings**プロパティの右側にあるボタンをクリックして、**テキスト**プロパティ、および選択**None**です。  
  
5.  `ProductNameListBox` コントロールを選択します。  
  
6.  **プロパティ** ウィンドウの右側にあるボタンをクリックして、**データソース**プロパティ、および選択**productsBindingSource**です。  
  
7.  右側にあるボタンをクリックして、 **DisplayMember**プロパティ、および選択**ProductName**です。  
  
8.  展開、 **DataBindings**プロパティの右側にあるボタンをクリックして、 **SelectedValue**プロパティ、および選択**None**です。  
  
## <a name="adding-a-method-to-insert-data-into-a-table"></a>テーブルにデータを挿入するメソッドを追加します。  
 次のタスクを開始、バインドされたコントロールからデータを読み取るし、Word 文書にテーブルを作成します。 まず、プロシージャ、テーブルの見出しの書式設定を作成し、追加、`AddData`メソッドを作成し、Word の表の書式を設定します。  
  
#### <a name="to-format-the-table-headings"></a>テーブルの見出しの書式を設定するには  
  
1.  `ActionsControl`クラス、テーブルの見出しの書式設定するメソッドを作成します。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
#### <a name="to-create-the-table"></a>テーブルを作成するには  
  
1.  `ActionsControl`クラス、1 つが存在する、[操作] ウィンドウからデータをテーブルに追加されていない場合に、テーブルを作成するメソッドを記述します。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
#### <a name="to-insert-text-into-a-word-table"></a>Word の表にテキストを挿入するには  
  
1.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、**挿入**ボタンをクリックします。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  C# でのイベント ハンドラーを作成する必要があります、<xref:System.Windows.Forms.Control.Click>ボタンのイベントです。  このコードを配置することができます、<xref:System.Windows.Forms.UserControl.Load>のイベント ハンドラー、`ActionsControl`クラスです。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="showing-the-actions-pane"></a>操作ウィンドウの表示  
 これにコントロールを追加した後、[操作] ウィンドウが表示されます。  
  
#### <a name="to-show-the-actions-pane"></a>[操作] ウィンドウを表示するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**ThisDocument.vb**または**ThisDocument.cs**、クリックして**コードの表示**ショートカット メニューの します。  
  
2.  上部にあるコントロールの新しいインスタンスを作成、`ThisDocument`クラスの次の例のように見えるようにします。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  コードを追加して、<xref:Microsoft.Office.Tools.Word.Document.Startup>のイベント ハンドラー`ThisDocument`次の例のように見えるようにします。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 これで、ドキュメントが開いているときに、操作ウィンドウが表示されることを確認するドキュメントをテストできます。 操作ウィンドウ上のコントロールにマスター/詳細リレーションシップをテストし、単語内のデータが表示されていることを確認時にテーブル、**挿入**ボタンをクリックします。  
  
#### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  [操作] ウィンドウが表示されていることを確認します。  
  
3.  コンボ ボックスに会社を選択し、いることを確認内の項目、**製品**ボックス変更を一覧表示します。  
  
4.  製品を選択し、をクリックして**挿入**操作 ウィンドウで、製品の詳細が単語内のテーブルに追加されたことを確認してください。  
  
5.  さまざまな企業から追加の製品を挿入します。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、Word の操作ウィンドウ上のコントロールへのデータのバインドの基礎を説明します。 ここでは、次の作業を行います。  
  
-   データを Excel でのコントロールをバインドします。 詳細については、次を参照してください。[チュートリアル: Excel の操作ウィンドウ上のコントロールへのデータ バインディング](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)です。  
  
-   プロジェクトを配置します。 詳細については、次を参照してください。 [ClickOnce を使用して Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)です。  
  
## <a name="see-also"></a>関連項目  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [方法: Word 文書や Excel ブックに操作ウィンドウを追加](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  