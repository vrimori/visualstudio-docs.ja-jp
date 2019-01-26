---
title: 'チュートリアル: データを Excel の操作ウィンドウ上のコントロールにバインドします。'
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d90250abdf727e47bbc9049b00e15a0f2b7978a7
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865841"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>チュートリアル: データを Excel の操作ウィンドウ上のコントロールにバインドします。
  このチュートリアルでは、Microsoft Office Excel で操作ウィンドウ上のコントロールへのデータ バインディングを示します。 このコントロールは、SQL Server データベースのテーブル間のマスター/詳細の関係を示します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   コントロールをワークシートに追加します。  
  
-   操作ウィンドウ コントロールを作成します。  
  
-   操作ウィンドウ コントロールにデータ バインド Windows フォーム コントロールを追加します。  
  
-   アプリケーションが開いたときに操作ウィンドウの表示。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   SQL Server の Northwind サンプル データベースでのサーバーへのアクセス。  
  
-   SQL Server データベースの読み書きアクセス許可。  
  
## <a name="create-the-project"></a>プロジェクトの作成  
 まず、Excel ブック プロジェクトを作成します。  
  
### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Excel ブック プロジェクトを作成する**マイ Excel 操作ウィンドウ**します。 ウィザードで、次のように選択します。**新しい文書を作成**です。 詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
     デザイナーで新しい Excel ブックを開き、**マイ Excel 操作ウィンドウ**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
## <a name="add-a-new-data-source-to-the-project"></a>プロジェクトに新しいデータ ソースを追加します。  
  
### <a name="to-add-a-new-data-source-to-the-project"></a>プロジェクトに新しいデータ ソースを追加するには  
  
1. 場合、**データソース**ウィンドウが表示されない、メニュー バーで 表示することによって、**ビュー** > **その他の Windows**  >  **データ ソース**します。  
  
2. **[新しいデータ ソースの追加]** をクリックして **データ ソース構成ウィザード**を開始します。  
  
3. 選択**データベース**順にクリックします**次**します。  
  
4. Northwind サンプル SQL Server データベースへのデータ接続を選択するかを使用して新しい接続を追加、**新しい接続**ボタンをクリックします。  
  
5. **[次へ]** をクリックします。  
  
6. クリックしてが選択されている場合、接続を保存するオプションをオフに**次**します。  
  
7. 展開、**テーブル**内のノード、**データベース オブジェクト**ウィンドウ。  
  
8. 次のチェック ボックスをオン、 **Suppliers**テーブル。  
  
9. 展開、**製品**テーブルを選択**ProductName**、 **SupplierID**、 **QuantityPerUnit**、および**UnitPrice**.  
  
10. **[完了]** をクリックします。  
  
    ウィザードでは追加、 **Suppliers**テーブルと**製品**テーブル、**データ ソース**ウィンドウ。 表示されているプロジェクトに型指定されたデータセットを追加**ソリューション エクスプ ローラー**します。  
  
## <a name="add-controls-to-the-worksheet"></a>ワークシートにコントロールを追加します。  
 次に、追加、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールと<xref:Microsoft.Office.Tools.Excel.ListObject>最初のワークシートにコントロール。  
  
### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>NamedRange コントロールと ListObject コントロールを追加するには  
  
1.  いることを確認、**マイ Excel アクション Pane.xlsx** 、Visual Studio デザイナーで開いているブックで`Sheet1`が表示されます。  
  
2.  **データソース**ウィンドウで、展開、 **Suppliers**テーブル。  
  
3.  ドロップダウン矢印をクリックして、**会社名**ノード、およびクリック**NamedRange**します。  
  
4.  ドラッグ**会社名**から、**データソース**セルにウィンドウ**A2**で`Sheet1`します。  
  
     A<xref:Microsoft.Office.Tools.Excel.NamedRange>という名前のコントロール`CompanyNameNamedRange`が作成されると、テキスト\<CompanyName > のセルに表示**A2**します。 、同時に、<xref:System.Windows.Forms.BindingSource>という名前`suppliersBindingSource`、テーブル アダプターの場合は、および<xref:System.Data.DataSet>、プロジェクトに追加されます。 コントロールにバインドする、<xref:System.Windows.Forms.BindingSource>にさらにバインドされます、<xref:System.Data.DataSet>インスタンス。  
  
5.  **データソース**ウィンドウで、過去の下にある列の下へスクロール、 **Suppliers**テーブル。 一覧の下部には、**製品**; テーブルの子であるため、ここでは、 **Suppliers**テーブル。 このオプションを選択**製品**テーブルと同じレベルでは、1 つない、 **Suppliers**テーブル、および、表示されるドロップダウン矢印をクリックします。  
  
6.  をクリックして**ListObject**をドラッグし、ドロップダウン一覧で、**製品**テーブル セルに**A6**で`Sheet1`します。  
  
     A<xref:Microsoft.Office.Tools.Excel.ListObject>という名前のコントロール`ProductNameListObject`セルは**A6**します。 、同時に、<xref:System.Windows.Forms.BindingSource>という`productsBindingSource`テーブル アダプターは、プロジェクトに追加されます。 コントロールにバインドする、<xref:System.Windows.Forms.BindingSource>にさらにバインドされます、<xref:System.Data.DataSet>インスタンス。  
  
7.  C# の場合のみ、次のように選択します**場合**コンポーネント トレイ上、**修飾子**プロパティを**内部**で、 **プロパティ。** ウィンドウ。  
  
## <a name="add-controls-to-the-actions-pane"></a>[操作] ウィンドウにコントロールを追加します。  
 次に、コンボ ボックスのある操作ウィンドウ コントロールする必要があります。  
  
### <a name="to-add-an-actions-pane-control"></a>操作ウィンドウ コントロールを追加するには  
  
1.  選択、**マイ Excel 操作ウィンドウ**プロジェクト**ソリューション エクスプ ローラー**します。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
3.  **新しい項目の追加**ダイアログ ボックスで、**操作ウィンドウ コントロール**、名前を付けます**ActionsControl**、 をクリック**追加**します。  
  
### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>操作ウィンドウ コントロールにデータ バインド Windows フォーム コントロールを追加するには  
  
1.  **コモン コントロール**のタブ、**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.ComboBox>操作ウィンドウ コントロールを制御します。  
  
2.  変更、**サイズ**プロパティを**171, 21**します。  
  
3.  コンボ ボックスに合わせてユーザー コントロールのサイズを変更します。  
  
## <a name="bind-the-control-on-the-actions-pane-to-data"></a>[操作] ウィンドウでコントロールをデータにバインドします。  
 このセクションでのデータ ソースを設定する、<xref:System.Windows.Forms.ComboBox>と同じデータ ソースに、<xref:Microsoft.Office.Tools.Excel.NamedRange>ワークシート上のコントロール。  
  
### <a name="to-set-data-binding-properties-of-the-control"></a>コントロールのデータ バインディングのプロパティを設定するには  
  
1.  操作ウィンドウ コントロールを右クリックし、をクリックし、**コードの表示**します。  
  
2.  次のコードを追加、<xref:System.Windows.Forms.UserControl.Load>操作ウィンドウ コントロールのイベント。  
  
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]  
  
3.  C# でのイベント ハンドラーを作成する必要があります、`ActionsControl`します。 このコードを配置することができます、`ActionsControl`コンス トラクター。 イベント ハンドラーの作成の詳細については、次を参照してください。[方法。Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]  
  
## <a name="show-the-actions-pane"></a>[操作] ウィンドウを表示します。  
 [操作] ウィンドウは、実行時にコントロールを追加するまで表示されません。  
  
#### <a name="to-show-the-actions-pane"></a>[操作] ウィンドウを表示するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして*ThisWorkbook.vb*または*ThisWorkbook.cs*、 をクリックし、**コードの表示**します。  
  
2.  内のユーザー コントロールの新しいインスタンスを作成、`ThisWorkbook`クラス。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]  
  
3.  <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>イベント ハンドラーの`ThisWorkbook`、[操作] ウィンドウにコントロールを追加します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
 これで、ドキュメントを開いたときに、[操作] ウィンドウを開き、コントロールの間にマスター/詳細関係があることを確認するドキュメントをテストできます。  
  
### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  キーを押して**F5**プロジェクトを実行します。  
  
2.  [操作] ウィンドウが表示されていることを確認します。  
  
3.  リスト ボックスで、会社を選択します。 会社名が表示されていることを確認、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールと製品の詳細が記載されている、<xref:Microsoft.Office.Tools.Excel.ListObject>コントロール。  
  
4.  会社名を確認するさまざまな企業を選択し、製品の詳細を必要に応じて変更します。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、次のタスクを行います。  
  
-   Word 内のコントロールにデータをバインドします。 詳細については、「[チュートリアル:Word の操作ウィンドウ上のコントロールにデータをバインド](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)します。  
  
-   プロジェクトを配置します。 詳細については、次を参照してください。 [ClickOnce を使用して Office ソリューションを配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)します。  
  
## <a name="see-also"></a>関連項目  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [方法: アクション ペイン上のコントロールのレイアウトを管理します。](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)  
