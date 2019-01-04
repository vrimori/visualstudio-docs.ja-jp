---
title: 'チュートリアル: Word の操作ウィンドウ上のコントロールにデータをバインドします。'
ms.date: 02/02/2017
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a113cbdffffb202a832ce145c4507bf5845ff52d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926451"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>チュートリアル: Word の操作ウィンドウ上のコントロールにデータをバインドします。
  このチュートリアルでは、Word の操作ウィンドウ上のコントロールへのデータ バインディングを示します。 このコントロールは、SQL Server データベースのテーブル間のマスター/詳細の関係を示します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   データにバインドされている Windows フォーム コントロールの操作ウィンドウを作成します。  
  
-   マスター/詳細リレーションシップを使用して、コントロールにデータを表示します。  
  
-   アプリケーションを開いたときに、[操作] ウィンドウを表示します。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
-   SQL Server の Northwind サンプル データベースでのサーバーへのアクセス。  
  
-   SQL Server データベースの読み書きアクセス許可。  
  
## <a name="create-the-project"></a>プロジェクトの作成  
 最初に、Word 文書のプロジェクトを作成します。  
  
### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Word 文書プロジェクトを作成**My Word の操作ウィンドウ**します。 ウィザードで、次のように選択します。**新しい文書を作成**です。  
  
     詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
     デザイナーで新しい Word 文書を開き、 **My Word の操作ウィンドウ**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
## <a name="add-controls-to-the-actions-pane"></a>[操作] ウィンドウにコントロールを追加します。  
 このチュートリアルでは、データ バインド Windows フォーム コントロールを含む操作ウィンドウ コントロールが必要です。 プロジェクトにデータ ソースを追加し、後からコントロールをドラッグ、**データソース**操作ウィンドウ コントロールにウィンドウ。  
  
### <a name="to-add-an-actions-pane-control"></a>操作ウィンドウ コントロールを追加するには  
  
1.  選択、 **My Word の操作ウィンドウ**プロジェクト**ソリューション エクスプ ローラー**します。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
3.  **新しい項目の追加**ダイアログ ボックスで、**操作ウィンドウ コントロール**、名前を付けます**ActionsControl**、 をクリックし、**追加**。  
  
### <a name="to-add-a-data-source-to-the-project"></a>データ ソースをプロジェクトに追加するには  
  
1. 場合、**データソース**ウィンドウが表示されない、メニュー バーで 表示することによって、**ビュー** > **その他の Windows**  >  **データ ソース**します。  
  
   > [!NOTE]  
   >  場合**データ ソースの**使用できない場合、Word 文書をクリックし、もう一度確認します。  
  
2. クリックして**新しいデータ ソースの追加**を開始する、**データ ソース構成ウィザード**します。  
  
3. 選択**データベース**順にクリックします**次**します。  
  
4. Northwind サンプル SQL Server データベースへのデータ接続を選択するかを使用して新しい接続を追加、**新しい接続**ボタンをクリックします。  
  
5. **[次へ]** をクリックします。  
  
6. クリックしてが選択されている場合、接続を保存するオプションをオフに**次**します。  
  
7. 展開、**テーブル**内のノード、**データベース オブジェクト**ウィンドウ。  
  
8. 次のチェック ボックスをオン、 **Suppliers**と**製品**テーブル。  
  
9. **[完了]** をクリックします。  
  
   ウィザードでは追加、 **Suppliers**テーブルと**製品**テーブル、**データ ソース**ウィンドウ。 表示されているプロジェクトに型指定されたデータセットを追加**ソリューション エクスプ ローラー**します。  
  
### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>操作ウィンドウ コントロールにデータ バインド Windows フォーム コントロールを追加するには  
  
1.  **データソース**ウィンドウで、展開、 **Suppliers**テーブル。  
  
2.  ドロップダウン矢印をクリックして、**会社名**ノード、および選択**ComboBox**します。  
  
3.  ドラッグ**CompanyName**から、**データソース**操作ウィンドウ コントロールにウィンドウ。  
  
     A<xref:System.Windows.Forms.ComboBox>操作ウィンドウ コントロールにコントロールが作成されます。 、同時に、<xref:System.Windows.Forms.BindingSource>という名前`SuppliersBindingSource`、テーブル アダプターの場合は、および<xref:System.Data.DataSet>コンポーネント トレイ内のプロジェクトに追加されます。  
  
4.  選択`SuppliersBindingNavigator`で、**コンポーネント**トレイとキーを押して**削除**します。 使用しない、`SuppliersBindingNavigator`このチュートリアルでします。  
  
    > [!NOTE]  
    >  削除、`SuppliersBindingNavigator`すべての生成されたコードは削除されません。 このコードを削除することができます。  
  
5.  ラベルと変更されるように、コンボ ボックスを移動、**サイズ**プロパティを**171, 21**します。  
  
6.  **データ ソース**ウィンドウで、展開、**製品**の子でテーブルには、 **Suppliers**テーブル。  
  
7.  ドロップダウン矢印をクリックして、 **ProductName**ノード、および選択**ListBox**します。  
  
8.  ドラッグ**ProductName**操作ウィンドウ コントロールにします。  
  
     A<xref:System.Windows.Forms.ListBox>操作ウィンドウ コントロールにコントロールが作成されます。 、同時に、<xref:System.Windows.Forms.BindingSource>という`ProductBindingSource`テーブル アダプターがコンポーネント トレイ内のプロジェクトに追加されます。  
  
9. ラベルと変更されるように、リスト ボックスを移動、**サイズ**プロパティを**171, 95**します。  
  
10. ドラッグ、<xref:System.Windows.Forms.Button>から、**ツールボックス**操作ウィンドウ上に制御し、リスト ボックスの下に配置します。  
  
11. 右クリックし、 <xref:System.Windows.Forms.Button>、 をクリックして**プロパティ**ショートカット メニューで、次のプロパティを変更するとします。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**[挿入]**|  
    |**[テキスト]**|**[挿入]**|  
  
12. コントロールに合わせてユーザー コントロールのサイズを変更します。  
  
## <a name="set-up-the-data-source"></a>データ ソースを設定します。  
 データ ソースを設定するには、コードを追加、<xref:System.Windows.Forms.UserControl.Load>からデータをコントロールに入力する操作ウィンドウ コントロールのイベント、 <xref:System.Data.DataTable>、設定、<xref:System.Windows.Forms.Binding.DataSource%2A>と<xref:System.Windows.Forms.BindingSource.DataMember%2A>各コントロールのプロパティ。  
  
### <a name="to-load-the-control-with-data"></a>コントロールにデータを読み込む  
  
1.  <xref:System.Windows.Forms.UserControl.Load>のイベント ハンドラー、`ActionsControl`クラスで、次のコードを追加します。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  C# でイベント ハンドラーをアタッチする必要があります、<xref:System.Windows.Forms.UserControl.Load>イベント。 このコードを配置することができます、`ActionsControl`コンス トラクターの呼び出しの後、`InitializeComponent`します。 イベント ハンドラーを作成する方法の詳細については、次を参照してください。[方法。Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
### <a name="to-set-data-binding-properties-of-the-controls"></a>コントロールのデータ バインディングのプロパティを設定するには  
  
1.  `CompanyNameComboBox` コントロールを選択します。  
  
2.  **プロパティ**ウィンドウの右ボタンをクリックして、**データソース**プロパティ、および選択**場合**。  
  
3.  右ボタンをクリックして、 **DisplayMember**プロパティ、および選択**CompanyName**します。  
  
4.  展開、 **DataBindings**プロパティの右側のボタンをクリックして、**テキスト**プロパティ、および選択**None**。  
  
5.  `ProductNameListBox` コントロールを選択します。  
  
6.  **プロパティ**ウィンドウの右ボタンをクリックして、**データソース**プロパティ、および選択**productsBindingSource**。  
  
7.  右ボタンをクリックして、 **DisplayMember**プロパティ、および選択**ProductName**します。  
  
8.  展開、 **DataBindings**プロパティの右側のボタンをクリックして、 **SelectedValue**プロパティ、および選択**None**。  
  
## <a name="add-a-method-to-insert-data-into-a-table"></a>テーブルにデータを挿入するメソッドを追加します。  
 次に、バインドされたコントロールからデータを読み取るし、Word 文書にテーブルを作成します。 まず、プロシージャ、テーブルの見出しの書式設定を作成し、追加、`AddData`メソッドを作成し、Word の表の書式を設定します。  
  
### <a name="to-format-the-table-headings"></a>テーブルの見出しの書式設定するには  
  
1.  `ActionsControl`クラス、テーブルの見出しの書式設定するメソッドを作成します。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
### <a name="to-create-the-table"></a>テーブルを作成するには  
  
1.  `ActionsControl`クラスを 1 つが存在する、[操作] ウィンドウからデータをテーブルに追加されていない場合にテーブルを作成するメソッドを記述します。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
### <a name="to-insert-text-into-a-word-table"></a>Word の表に、テキストを挿入するには  
  
1.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、**挿入**ボタンをクリックします。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  C# でのイベント ハンドラーを作成する必要があります、<xref:System.Windows.Forms.Control.Click>ボタンのイベント。  このコードを配置することができます、<xref:System.Windows.Forms.UserControl.Load>のイベント ハンドラー、`ActionsControl`クラス。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="show-the-actions-pane"></a>[操作] ウィンドウを表示します。  
 コントロールを追加した後、[操作] ウィンドウが表示されます。  
  
### <a name="to-show-the-actions-pane"></a>[操作] ウィンドウを表示するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**ThisDocument.vb**または**ThisDocument.cs**、] をクリックし、**コードの表示**ショートカット メニューの [します。  
  
2.  上部にあるコントロールの新しいインスタンスを作成、`ThisDocument`クラスに次の例のようになります。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  コードを追加して、<xref:Microsoft.Office.Tools.Word.Document.Startup>イベント ハンドラーの`ThisDocument`次の例のように見えるようにします。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
 これで、ドキュメントが開いているときに、操作ウィンドウが表示されることを確認するドキュメントをテストできます。 単語内のデータが表示されているかどうかを確認して、操作ウィンドウ上のコントロールのマスター/詳細リレーションシップをテスト時にテーブル、**挿入**ボタンをクリックします。  
  
### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  キーを押して**F5**プロジェクトを実行します。  
  
2.  [操作] ウィンドウが表示されていることを確認します。  
  
3.  コンボ ボックスに会社を選択し、いることを確認内の項目、**製品**ボックスの一覧を表示します。  
  
4.  製品を選択して、**挿入**操作ウィンドウで、Word の表に、製品の詳細が追加されたことを確認します。  
  
5.  さまざまな企業から、その他の製品を挿入します。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、Word の操作ウィンドウ上のコントロールへのデータ バインディングの基礎を説明します。 ここでは、次のタスクを行います。  
  
-   データを Excel でのコントロールをバインドします。 詳細については、「[チュートリアル:Excel の操作ウィンドウ上のコントロールにデータをバインド](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)します。  
  
-   プロジェクトを配置します。 詳細については、次を参照してください。 [ClickOnce を使用して Office ソリューションを配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)します。  
  
## <a name="see-also"></a>関連項目  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [方法: Word 文書または Excel ブックに操作ウィンドウを追加します。](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)  
