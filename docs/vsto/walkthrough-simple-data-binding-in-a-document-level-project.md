---
title: 'チュートリアル: ドキュメント レベルのプロジェクトでの単純なデータ バインディング'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25173e5c4d4aeb02045cf858ae1e093b7a04d2bb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824381"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>チュートリアル: ドキュメント レベルのプロジェクトでの単純なデータ バインディング
  このチュートリアルでは、ドキュメント レベルのプロジェクトでのデータ バインディングの基本について説明します。 SQL Server データベースの 1 つのデータ フィールドは、Microsoft Office Excel で名前付き範囲にバインドされます。 このチュートリアルでは、テーブル内のすべてのレコードをスクロールするためのコントロールを追加する方法も示します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
- Excel プロジェクトのデータ ソースを作成します。  
  
- コントロールをワークシートに追加します。  
  
- データベースのレコードをスクロールします。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   SQL Server の Northwind サンプル データベースでのサーバーへのアクセス。  
  
-   SQL Server データベースの読み書きアクセス許可。  
  
## <a name="create-a-new-project"></a>新しいプロジェクトを作成する  
 この手順では、Excel ブック プロジェクトを作成します。  
  
### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1. 名前の Excel ブック プロジェクトを作成**マイの単純データ バインディング**、Visual Basic または c# を使用します。 必ず**新しい文書を作成**が選択されています。 詳細については、次の[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)を参照してください。  
  
   デザイナーで新しい Excel ブックを開き、**マイの単純データ バインディング**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
## <a name="create-the-data-source"></a>データ ソースを作成します。  
 **[データ ソース]** ウィンドウを使用して、型指定されたデータセットをプロジェクトに追加します。  
  
### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1. 場合、**データソース**ウィンドウが表示されない、メニュー バーで 表示することによって、**ビュー** > **その他の Windows**  >  **データ ソース**します。  
  
2. **[新しいデータ ソースの追加]** をクリックして **データ ソース構成ウィザード**を開始します。  
  
3. 選択**データベース**順にクリックします**次**します。  
  
4. Northwind サンプルの SQL Server データベースへのデータ接続を選択するか使用して新しい接続を追加、**新しい接続**ボタンをクリックします。  
  
5. 接続を選択または作成後にをクリックして**次**します。  
  
6. クリックしてが選択されている場合、接続を保存するオプションをオフに**次**します。  
  
7. 展開、**テーブル**内のノード、**データベース オブジェクト**ウィンドウ。  
  
8. 次のチェック ボックスをオン、**顧客**テーブル。  
  
9. **[完了]** をクリックします。  
  
   ウィザードでは追加、**顧客**テーブル、**データ ソース**ウィンドウ。 表示されているプロジェクトに型指定されたデータセットを追加**ソリューション エクスプ ローラー**します。  
  
## <a name="add-controls-to-the-worksheet"></a>ワークシートにコントロールを追加します。  
 このチュートリアルでは、2 つの名前付き範囲と最初のワークシートに 4 つのボタンが必要です。 最初に、2 つの名前付き範囲を追加、**データソース**ウィンドウ データ ソースに自動的にバインドされているようにします。 次からボタンを追加、**ツールボックス**します。  
  
### <a name="to-add-two-named-ranges"></a>2 つの名前付き範囲を追加するには  
  
1.  いることを確認、*マイの単純なデータ Binding.xlsx* 、Visual Studio デザイナーで開いているブックで**Sheet1**が表示されます。  
  
2.  開く、**データ ソース**ウィンドウを展開し、**顧客**ノード。  
  
3.  選択、 **CompanyName**列で、表示されるドロップダウン矢印を順にクリックします。  
  
4.  選択**NamedRange**をドラッグし、ドロップダウン一覧で、 **CompanyName**セルに列**A1**します。  
  
     A<xref:Microsoft.Office.Tools.Excel.NamedRange>という名前のコントロール`companyNameNamedRange`セルは**A1**します。 、同時に、<xref:System.Windows.Forms.BindingSource>という名前`customersBindingSource`、テーブル アダプターの場合は、および<xref:System.Data.DataSet>インスタンスは、プロジェクトに追加されます。 コントロールにバインドする、<xref:System.Windows.Forms.BindingSource>にさらにバインドされます、<xref:System.Data.DataSet>インスタンス。  
  
5.  選択、 **CustomerID**内の列、**データ ソース**ウィンドウで、表示されるドロップダウン リストの下矢印をクリックします。  
  
6.  クリックして**NamedRange**をドラッグし、ドロップダウン一覧で、 **CustomerID**セルに列**B1**します。  
  
7.  もう 1 つ<xref:Microsoft.Office.Tools.Excel.NamedRange>という名前のコントロール`customerIDNamedRange`セルは**B1**にバインドされていると、 <xref:System.Windows.Forms.BindingSource>。  
  
### <a name="to-add-four-buttons"></a>4 つのボタンを追加するには  
  
1. **コモン コントロール**のタブ、**ツールボックス**、追加、<xref:System.Windows.Forms.Button>コントロールをセル**A3**ワークシートの。  
  
    このボタンの名前は`Button1`します。  
  
2. 名前が示すようになるように、次の順序で次のセルに他の 3 つのボタンを追加します。  
  
   |セル|(名前)|  
   |----------|--------------|  
   |B3|Button2|  
   |C3|Button3|  
   |D3|Button4|  
  
   次の手順では、ボタンにテキストを追加し、c# でイベント ハンドラーを追加します。  
  
## <a name="initialize-the-controls"></a>コントロールを初期化します。  
 ボタン テキストを設定し、中にイベント ハンドラーを追加、<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>イベント。  
  
### <a name="to-initialize-the-controls"></a>コントロールを初期化するには  
  
1. **ソリューション エクスプ ローラー**を右クリックして**Sheet1.vb**または**Sheet1.cs**、] をクリックし、**コードの表示**ショートカット メニューの [します。  
  
2. 次のコードを追加、`Sheet1_Startup`各ボタンのテキストを設定します。  
  
    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]  
  
3. C# の場合のみ、追加ボタンのイベント ハンドラーにイベントをクリックして、`Sheet1_Startup`メソッド。  
  
    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]  
  
   今すぐ処理するコードを追加、<xref:System.Windows.Forms.Control.Click>ボタンのイベント、ユーザーがレコードを閲覧できるようにします。  
  
## <a name="add-code-to-enable-scrolling-through-the-records"></a>レコードのスクロールを有効にするコードを追加します。  
 コードを追加して、<xref:System.Windows.Forms.Control.Click>レコード間を移動するには、各ボタンのイベント ハンドラー。  
  
### <a name="to-move-to-the-first-record"></a>最初のレコードを移動するには  
  
1.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Control.Click>のイベント、`Button1`ボタンをクリックし、最初のレコードを移動するには、次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]  
  
### <a name="to-move-to-the-previous-record"></a>前のレコードに移動するには  
  
1.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Control.Click>のイベント、`Button2`ボタンをクリックし、いずれかで位置を戻すには、次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]  
  
### <a name="to-move-to-the-next-record"></a>次のレコードに移動するには  
  
1.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Control.Click>のイベント、`Button3`ボタンをクリックし、次のコードを 1 つの位置を進めますを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]  
  
### <a name="to-move-to-the-last-record"></a>最後のレコードに移動するには  
  
1.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Control.Click>のイベント、`Button4`ボタンをクリックし、最後のレコードに移動するには、次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
 データベース内のレコードを参照できることを確認するブックをテストできます。  
  
### <a name="to-test-your-workbook"></a>ブックをテストするには  
  
1.  キーを押して**F5**プロジェクトを実行します。  
  
2.  セルの最初のレコードが表示されることを確認します。 **A1**と**B1**します。  
  
3.  をクリックして、 **>** (`Button3`) ボタンをクリックし、次のレコードがセルに表示されることを確認します。 **A1**と**B1**します。  
  
4.  レコードが期待どおりに変わることを確認するその他のスクロール ボタンをクリックします。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、データベース内のフィールドに名前付き範囲のバインドの基本を説明します。 ここでは、次のタスクを行います。  
  
-   データをキャッシュにオフラインで使用できるようにします。 詳細については、次を参照してください。[方法: オフラインか、サーバーで使用するデータをキャッシュ](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)します。  
  
-   代わりに、テーブル内の複数の列にセルを 1 つのフィールドにバインドします。 詳細については、次を参照してください。[チュートリアル: ドキュメント レベルのプロジェクトで複合データ バインディング](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)します。  
  
-   使用して、<xref:System.Windows.Forms.BindingNavigator>コントロール、レコード間をスクロールします。 詳細については、次を参照してください。[方法: Windows フォーム BindingNavigator コントロールを使用してデータを移動](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [チュートリアル: ドキュメント レベルのプロジェクトで複雑なデータ バインディング](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  