---
title: "チュートリアル: ドキュメント レベルのプロジェクトでの単純なデータ バインディング |Microsoft ドキュメント"
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
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
ms.assetid: 6b8fd638-af13-4ea1-b1c0-2763e2d8ae23
caps.latest.revision: "58"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 847b547aae785d94f8d9025b7b4badf9d8b21075
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>チュートリアル : ドキュメント レベルのプロジェクトでの単純データ バインディング
  このチュートリアルでは、ドキュメント レベルのプロジェクトでのデータ バインディングの基本について説明します。 SQL Server データベースの 1 つのデータ フィールドは、Microsoft Office Excel で名前付き範囲にバインドされています。 このチュートリアルでは、テーブル内のすべてのレコードをスクロールできるようにするコントロールを追加する方法も示します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   Excel プロジェクトのデータ ソースを作成します。  
  
-   コントロールをワークシートに追加します。  
  
-   データベース レコードをスクロールします。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   Northwind SQL Server サンプル データベースを持つサーバーにアクセスします。  
  
-   読み取りと書き込みの SQL Server データベースにアクセスを許可します。  
  
## <a name="creating-a-new-project"></a>新規プロジェクトの作成  
 このステップでは、Excel ブック プロジェクトを作成します。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Excel ブック プロジェクトを作成**マイの単純データ バインディング**、Visual Basic または c# を使用します。 確認して**新しいドキュメントを作成する**が選択されています。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
 デザイナーで新しい Excel ブックを開き、**マイの単純データ バインディング**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="creating-the-data-source"></a>データ ソースの作成  
 **[データ ソース]** ウィンドウを使用して、型指定されたデータセットをプロジェクトに追加します。  
  
#### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1.  **[データ ソース]** ウィンドウが表示されていない場合は、メニュー バーの **[表示]**、 **[その他のウィンドウ]**、 **[データ ソース]**の順にクリックして表示します。  
  
2.  **[新しいデータ ソースの追加]** をクリックして **データ ソース構成ウィザード**を開始します。  
  
3.  選択**データベース** をクリックし、**次**です。  
  
4.  Northwind サンプル SQL Server データベースへのデータ接続を選択するか、新しい接続を使用して、追加、**新しい接続**ボタンをクリックします。  
  
5.  接続を選択または作成した後にをクリックして**次**です。  
  
6.  クリックしてオンになっている場合、接続を保存するオプションをオフに**次**です。  
  
7.  展開して、**テーブル**内のノード、**データベース オブジェクト**ウィンドウです。  
  
8.  次のチェック ボックスをオン、**顧客**テーブル。  
  
9. **[完了]**をクリックします。  
  
 ウィザードでは追加、**顧客**テーブル、**データ ソース**ウィンドウです。 表示されているプロジェクトにも型指定されたデータセットを追加**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-controls-to-the-worksheet"></a>ワークシートへのコントロールの追加  
 このチュートリアルでは、次の 2 つの名前付き範囲と最初のワークシートに 4 つのボタンが必要です。 最初に、2 つの名前付き範囲を追加、**データ ソース**ウィンドウ、データ ソースに自動的にバインドされるようにします。 次に、追加のボタン、**ツールボックス**です。  
  
#### <a name="to-add-two-named-ranges"></a>2 つの名前付き範囲を追加するには  
  
1.  いることを確認、**マイの単純なデータ Binding.xlsx** 、Visual Studio デザイナーで開いているブックで**Sheet1**が表示されます。  
  
2.  開く、**データ ソース**ウィンドウを展開し、**顧客**ノード。  
  
3.  選択、 **CompanyName**列で、表示されるドロップダウン矢印をクリックします。  
  
4.  選択**NamedRange**をドラッグし、ドロップダウン一覧で、 **CompanyName**セルに列**A1**です。  
  
     A<xref:Microsoft.Office.Tools.Excel.NamedRange>という名前のコントロール`companyNameNamedRange`セルで作成された**A1**です。 同時に、<xref:System.Windows.Forms.BindingSource>という名前`customersBindingSource`、テーブルのアダプターでは、および<xref:System.Data.DataSet>インスタンスは、プロジェクトに追加されます。 コントロールがバインドされている、 <xref:System.Windows.Forms.BindingSource>、さらにこれがバインドに、<xref:System.Data.DataSet>インスタンス。  
  
5.  選択、 **CustomerID**内の列、**データ ソース**ウィンドウ、表示されるドロップダウン矢印をクリックします。  
  
6.  をクリックして**NamedRange**をドラッグし、ドロップダウン一覧で、 **CustomerID**セルに列**B1**です。  
  
7.  別<xref:Microsoft.Office.Tools.Excel.NamedRange>という名前のコントロール`customerIDNamedRange`セルで作成された**B1**にバインドされていると、<xref:System.Windows.Forms.BindingSource>です。  
  
#### <a name="to-add-four-buttons"></a>次の 4 つのボタンを追加するには  
  
1.  **コモン コントロール**のタブ、**ツールボックス**、追加、<xref:System.Windows.Forms.Button>コントロールをセル**A3**ワークシートのです。  
  
     このボタンの名前は`Button1`します。  
  
2.  名前が示すようになるように、この順序で次のセルに他の 3 つのボタンを追加します。  
  
    |セル|(名前)|  
    |----------|--------------|  
    |B3|Button2|  
    |C3|Button3|  
    |D3|Button4|  
  
 次の手順では、ボタンにテキストを追加し、c# でのイベント ハンドラーを追加します。  
  
## <a name="initializing-the-controls"></a>コントロールの初期化  
 ボタンのテキストを設定中にイベント ハンドラーを追加して、<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>イベント。  
  
#### <a name="to-initialize-the-controls"></a>コントロールを初期化するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**Sheet1.vb**または**Sheet1.cs**、クリックして**コードの表示**ショートカット メニューの します。  
  
2.  次のコードを追加、`Sheet1_Startup`の各ボタンのテキストを設定します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]  
  
3.  C# の場合のみ、追加、ボタンのイベント ハンドラーにイベントをクリックして、`Sheet1_Startup`メソッドです。  
  
     [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]  
  
 今すぐ処理するコードを追加、<xref:System.Windows.Forms.Control.Click>ボタンのイベントのレコードをユーザーが閲覧できるようにします。  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>レコードのスクロールを有効にするコードを追加します。  
 コードを追加して、<xref:System.Windows.Forms.Control.Click>レコード間を移動するには、各ボタンのイベント ハンドラー。  
  
#### <a name="to-move-to-the-first-record"></a>最初のレコードに移動するには  
  
1.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Control.Click>のイベント、`Button1`ボタンをクリックし、最初のレコードに移動する次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]  
  
#### <a name="to-move-to-the-previous-record"></a>前のレコードに移動するには  
  
1.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Control.Click>のイベント、`Button2`ボタンをクリックし、1 つの位置を戻すには、次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]  
  
#### <a name="to-move-to-the-next-record"></a>次のレコードに移動するには  
  
1.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Control.Click>のイベント、`Button3`ボタンをクリックし、いずれかで位置を進めますに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]  
  
#### <a name="to-move-to-the-last-record"></a>最後のレコードに移動するには  
  
1.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Control.Click>のイベント、`Button4`ボタンをクリックし、最後のレコードに移動するには、次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 データベース内のレコードを参照できることを確認するブックをテストできます。  
  
#### <a name="to-test-your-workbook"></a>ブックをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  最初のレコードがセルに表示されることを確認**A1**と**B1**です。  
  
3.  クリックして、  **>**  (`Button3`) ボタンをクリックし、次のレコードがセルに表示されていることを確認**A1**と**B1**です。  
  
4.  レコードが期待どおりに変わることを確認するその他のスクロール ボタンをクリックします。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、データベース内のフィールドに名前付き範囲のバインドの基礎を説明します。 ここでは、次の作業を行います。  
  
-   オフライン使用できるようにする、データをキャッシュします。 詳細については、次を参照してください。[する方法: オフラインで使用またはサーバー上にデータをキャッシュ](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)です。  
  
-   代わりに、テーブル内の複数の列にセルを 1 つのフィールドにバインドします。 詳細については、次を参照してください。[チュートリアル: ドキュメント レベルのプロジェクトでの複合データ バインディング](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)です。  
  
-   使用して、<xref:System.Windows.Forms.BindingNavigator>レコード間をスクロール コントロール。 詳細については、次を参照してください。[する方法: Windows フォーム BindingNavigator コントロールにデータを移動](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)です。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [チュートリアル: ドキュメント レベルのプロジェクトでの複合データ バインディング](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  