---
title: 'チュートリアル: Excel の操作ウィンドウ上のコントロールへのデータのバインド |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 87d960c01d8ac28b2a148e2f48ee51a877d97c20
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-binding-data-to-controls-on-an-excel-actions-pane"></a>チュートリアル : Excel のアクション ペインのコントロールへのデータ連結
  このチュートリアルでは、Microsoft Office Excel の操作ウィンドウ上のコントロールへのデータ バインディングを示します。 このコントロールは、SQL Server データベースのテーブル間のマスター/詳細の関係を示します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   コントロールをワークシートに追加します。  
  
-   操作ウィンドウ コントロールを作成します。  
  
-   操作ウィンドウ コントロールにデータ バインド Windows フォーム コントロールを追加します。  
  
-   アプリケーションを開いたときは、[操作] ウィンドウを表示します。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   Northwind SQL Server サンプル データベースを持つサーバーにアクセスします。  
  
-   読み取りと書き込みの SQL Server データベースにアクセスを許可します。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 まず、Excel ブック プロジェクトを作成します。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Excel ブック プロジェクトを作成**マイ Excel 操作ウィンドウ**します。 ウィザードで、次のように選択します。**新しいドキュメントを作成する**です。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     デザイナーで新しい Excel ブックを開き、**マイ Excel 操作ウィンドウ**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-a-new-data-source-to-the-project"></a>プロジェクトに新しいデータ ソースの追加  
  
#### <a name="to-add-a-new-data-source-to-the-project"></a>プロジェクトに新しいデータ ソースを追加するには  
  
1.  **[データ ソース]** ウィンドウが表示されていない場合は、メニュー バーの **[表示]**、 **[その他のウィンドウ]**、 **[データ ソース]**の順にクリックして表示します。  
  
2.  **[新しいデータ ソースの追加]** をクリックして **データ ソース構成ウィザード**を開始します。  
  
3.  選択**データベース** をクリックし、**次**です。  
  
4.  Northwind サンプル SQL Server データベースへのデータ接続を選択するかを使用して新しい接続を追加、**新しい接続**ボタンをクリックします。  
  
5.  **[次へ]**をクリックします。  
  
6.  クリックしてオンになっている場合、接続を保存するオプションをオフに**次**です。  
  
7.  展開して、**テーブル**内のノード、**データベース オブジェクト**ウィンドウです。  
  
8.  次のチェック ボックスをオン、 **Suppliers**テーブル。  
  
9. 展開して、**製品**テーブルを選択して**ProductName**、 **SupplierID**、 **QuantityPerUnit**、および**UnitPrice**.  
  
10. **[完了]**をクリックします。  
  
 ウィザードでは追加、 **Suppliers**テーブルと**製品**テーブル、**データ ソース**ウィンドウです。 表示されているプロジェクトにも型指定されたデータセットを追加**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-controls-to-the-worksheet"></a>ワークシートへのコントロールの追加  
 次に、追加、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールと<xref:Microsoft.Office.Tools.Excel.ListObject>最初のワークシートにコントロールできます。  
  
#### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>NamedRange コントロールと ListObject コントロールを追加するには  
  
1.  いることを確認、**マイ Excel アクション Pane.xlsx** 、Visual Studio デザイナーで開いているブックで`Sheet1`が表示されます。  
  
2.  **データソース**ウィンドウで、展開、 **Suppliers**テーブル。  
  
3.  ドロップダウン矢印をクリックして、**会社名**ノードをクリックして**NamedRange**です。  
  
4.  ドラッグ**会社名**から、**データソース**セルにウィンドウ**A2**で`Sheet1`です。  
  
     A<xref:Microsoft.Office.Tools.Excel.NamedRange>という名前のコントロール`CompanyNameNamedRange`が作成されると、テキスト\<CompanyName > セルに表示されます**A2**です。 同時に、<xref:System.Windows.Forms.BindingSource>という名前`suppliersBindingSource`、テーブルのアダプターでは、および<xref:System.Data.DataSet>プロジェクトに追加されます。 コントロールがバインドされている、 <xref:System.Windows.Forms.BindingSource>、さらにこれがバインドに、<xref:System.Data.DataSet>インスタンス。  
  
5.  **データソース**ウィンドウで、過去の下にある列をスクロールして、 **Suppliers**テーブル。 一覧の下部には、**製品**テーブルです。 ここでは、の子になっているため、 **Suppliers**テーブル。 このオプションを選択**製品**テーブルと同じレベルにあるものではなく、 **Suppliers**テーブル、および、表示されるドロップダウン矢印をクリックします。  
  
6.  をクリックして**ListObject**をドラッグし、ドロップダウン一覧で、**製品**テーブル セルに**A6**で`Sheet1`です。  
  
     A<xref:Microsoft.Office.Tools.Excel.ListObject>という名前のコントロール`ProductNameListObject`セルで作成された**A6**です。 同時に、<xref:System.Windows.Forms.BindingSource>という`productsBindingSource`されテーブル アダプターは、プロジェクトに追加されます。 コントロールがバインドされている、 <xref:System.Windows.Forms.BindingSource>、さらにこれがバインドに、<xref:System.Data.DataSet>インスタンス。  
  
7.  C# の場合のみ、次のように選択します**場合**コンポーネント トレイ、および変更、**修飾子**プロパティを**内部**で、 **のプロパティ。**ウィンドウです。  
  
## <a name="adding-controls-to-the-actions-pane"></a>[操作] ウィンドウにコントロールを追加します。  
 次に、操作ウィンドウ コントロールをコンボ ボックスを含む必要があります。  
  
#### <a name="to-add-an-actions-pane-control"></a>操作ウィンドウ コントロールを追加するには  
  
1.  選択、**マイ Excel 操作ウィンドウ**プロジェクト**ソリューション エクスプ ローラー**です。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
3.  **新しい項目の追加**ダイアログ ボックスで、**操作ウィンドウ コントロール**、名前を付けます**ActionsControl**、 をクリック**追加**です。  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>操作ウィンドウ コントロールにデータ バインド Windows フォーム コントロールを追加するには  
  
1.  **コモン コントロール**のタブ、**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.ComboBox>操作ウィンドウ コントロールを制御します。  
  
2.  変更、**サイズ**プロパティを**171, 21**です。  
  
3.  コンボ ボックスに合わせて、ユーザー コントロールのサイズを変更します。  
  
## <a name="binding-the-control-on-the-actions-pane-to-data"></a>[操作] ウィンドウでコントロールをデータにバインドします。  
 このセクションでは、データ ソースを設定します、<xref:System.Windows.Forms.ComboBox>と同じデータ ソースに、<xref:Microsoft.Office.Tools.Excel.NamedRange>ワークシート上のコントロールです。  
  
#### <a name="to-set-data-binding-properties-of-the-control"></a>コントロールのデータ バインディング プロパティを設定するには  
  
1.  操作ウィンドウ コントロールを右クリックし、をクリックして**コードの表示**です。  
  
2.  次のコードを追加、<xref:System.Windows.Forms.UserControl.Load>操作ウィンドウ コントロールのイベントです。  
  
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]  
  
3.  C# でのイベント ハンドラーを作成する必要があります、`ActionsControl`です。 このコードを配置することができます、`ActionsControl`コンス トラクターです。 イベント ハンドラーの作成の詳細については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]  
  
## <a name="showing-the-actions-pane"></a>操作ウィンドウの表示  
 [操作] ウィンドウは、実行時にコントロールを追加するまでは表示されません。  
  
#### <a name="to-show-the-actions-pane"></a>[操作] ウィンドウを表示するには  
  
1.  **ソリューション エクスプ ローラー**ThisWorkbook.vb または ThisWorkbook.cs を右クリックし、クリックして**コードの表示**です。  
  
2.  内のユーザー コントロールの新しいインスタンスを作成、`ThisWorkbook`クラスです。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]  
  
3.  <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>のイベント ハンドラー `ThisWorkbook`、[操作] ウィンドウにコントロールを追加します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 ここで、ドキュメントを開いたときに、[操作] ウィンドウを開き、コントロールの間にマスター/詳細関係があることを確認する文書をテストできます。  
  
#### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  [操作] ウィンドウが表示されていることを確認します。  
  
3.  リスト ボックスで、会社を選択します。 会社名が表示されていることを確認してください、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールと製品の詳細が記載されている、<xref:Microsoft.Office.Tools.Excel.ListObject>コントロール。  
  
4.  会社名を検証するさまざまな企業を選択し、製品の詳細を必要に応じて変更します。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、次のタスクを行います。  
  
-   単語内のコントロールにデータをバインドします。 詳細については、次を参照してください。[チュートリアル: Word の操作ウィンドウ上のコントロールへのデータ バインディング](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)です。  
  
-   プロジェクトを配置します。 詳細については、次を参照してください。 [ClickOnce を使用して Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)です。  
  
## <a name="see-also"></a>関連項目  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [方法: アクション ペイン上のコントロールのレイアウトの管理](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  