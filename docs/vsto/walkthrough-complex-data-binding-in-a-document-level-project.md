---
title: 'チュートリアル: ドキュメント レベルのプロジェクトで複合データ バインディング'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5da24d43173a0124849855bf9184f3a823230d3a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865009"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>チュートリアル: ドキュメント レベルのプロジェクトで複合データ バインディング
  このチュートリアルでは、ドキュメント レベルのプロジェクトで複合データ バインディングの基本について説明します。 Microsoft Office Excel ワークシート内で複数のセルは、Northwind SQL Server データベース内のフィールドにバインドできます。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
- データ ソースのブック プロジェクトに追加します。  
  
- データ バインド コントロールをワークシートに追加します。  
  
- 元のデータベースには、データの変更を保存しています。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   SQL Server の Northwind サンプル データベースでのサーバーへのアクセス。  
  
-   SQL Server データベースの読み書きアクセス許可。  
  
## <a name="create-a-new-project"></a>新しいプロジェクトを作成する  
 最初の手順では、Excel ブック プロジェクトを作成します。  
  
### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Excel ブック プロジェクトを作成**マイの複合データ バインディング**します。 ウィザードで、次のように選択します。**新しい文書を作成**です。  
  
     詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
     デザイナーで新しい Excel ブックを開き、**マイの複合データ バインディング**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
## <a name="create-the-data-source"></a>データ ソースを作成します。  
 **[データ ソース]** ウィンドウを使用して、型指定されたデータセットをプロジェクトに追加します。  
  
### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1. 場合、**データソース**ウィンドウが表示されない、メニュー バーで 表示することによって、**ビュー** > **その他の Windows**  >  **データ ソース**します。  
  
2. **[新しいデータ ソースの追加]** をクリックして **データ ソース構成ウィザード**を開始します。  
  
3. 選択**データベース**順にクリックします**次**します。  
  
4. Northwind サンプル SQL Server データベースへのデータ接続を選択するかを使用して新しい接続を追加、**新しい接続**ボタンをクリックします。  
  
5. 接続を選択または作成後にをクリックして**次**します。  
  
6. クリックしてが選択されている場合、接続を保存するオプションをオフに**次**します。  
  
7. 展開、**テーブル**内のノード、**データベース オブジェクト**ウィンドウ。  
  
8. 次のチェック ボックスをオン、**従業員**テーブル。  
  
9. **[完了]** をクリックします。  
  
   ウィザードでは追加、**従業員**テーブル、**データ ソース**ウィンドウ。 表示されているプロジェクトに型指定されたデータセットを追加**ソリューション エクスプ ローラー**します。  
  
## <a name="add-controls-to-the-worksheet"></a>ワークシートにコントロールを追加します。  
 ワークシートが表示されます、**従業員**ブックを開いたときにテーブルです。 ユーザーは、データに変更を加えるし、データベースに戻すボタンをクリックしてそれらの変更を保存することになります。  
  
 テーブルに自動的にワークシートをバインドするに追加することができます、<xref:Microsoft.Office.Tools.Excel.ListObject>からワークシートにコントロール、**データソース**ウィンドウ。 ユーザーに提供する、変更を保存するオプションを追加、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**します。  
  
#### <a name="to-add-a-list-object"></a>リスト オブジェクトを追加するには  
  
1.  いることを確認、**マイの複雑なデータ Binding.xlsx** 、Visual Studio デザイナーで開いているブックで**Sheet1**が表示されます。  
  
2.  開く、**データソース**ウィンドウと選択、**従業員**ノード。  
  
3.  表示されるドロップダウン矢印をクリックします。  
  
4.  選択**ListObject**ドロップダウン リストでします。  
  
5.  ドラッグ、**従業員**テーブル セルに**A6**します。  
  
     A<xref:Microsoft.Office.Tools.Excel.ListObject>という名前のコントロール`EmployeesListObject`セルは**A6**します。 、同時に、<xref:System.Windows.Forms.BindingSource>という名前`EmployeesBindingSource`、テーブル アダプターの場合は、および<xref:System.Data.DataSet>インスタンスは、プロジェクトに追加されます。 コントロールにバインドする、<xref:System.Windows.Forms.BindingSource>にさらにバインドされます、<xref:System.Data.DataSet>インスタンス。  
  
### <a name="to-add-a-button"></a>ボタンを追加するには  
  
1. **コモン コントロール**のタブ、**ツールボックス**、追加、<xref:System.Windows.Forms.Button>コントロールをセル**A4**ワークシートの。  
  
   次の手順では、ワークシートが開いたら、ボタンにテキストを追加します。  
  
## <a name="initialize-the-control"></a>コントロールを初期化します。  
 テキスト、ボタンを追加、<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>イベント ハンドラー。  
  
### <a name="to-initialize-the-control"></a>コントロールを初期化するには  
  
1. **ソリューション エクスプ ローラー**を右クリックして**Sheet1.vb**または**Sheet1.cs**、] をクリックし、**コードの表示**ショートカット メニューの [します。  
  
2. 次のコードを追加、 `Sheet1_Startup` 、b のテキストを設定するメソッドを`utton`します。  
  
    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]  
  
3. C# の場合のみ、追加のイベント ハンドラー、<xref:System.Windows.Forms.Control.Click>イベントを`Sheet1_Startup`メソッド。  
  
    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]  
  
   今すぐ処理するコードを追加、<xref:System.Windows.Forms.Control.Click>ボタンのイベント。  
  
## <a name="save-changes-to-the-database"></a>変更をデータベースに保存します。  
 すべての変更を加え、データベースに明示的に保存されるまでに、データがローカル データセットにのみ存在します。  
  
### <a name="to-save-changes-to-the-database"></a>データベースに変更を保存するには  
  
1.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Control.Click>のイベント、`button`データセットの元のデータベースに行われたすべての変更をコミットする次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
 これで、想定どおりにデータが表示されることと、リスト オブジェクト内のデータを操作できることを確認するブックをテストできます。  
  
### <a name="to-test-the-data-binding"></a>データ バインドをテストするには  
  
-   **F5**キーを押します。  
  
     ブックを開いたときに、リスト オブジェクトがからデータが入力されていることを確認、**従業員**テーブル。  
  
### <a name="to-modify-data"></a>データを変更するには  
  
1.  セルをクリックします。 **B7**、名前を格納する必要があります**Davolio**します。  
  
2.  名前を入力します**Anderson**、し、キーを押します**Enter**します。  
  
### <a name="to-modify-a-column-header"></a>列ヘッダーを変更するには  
  
1.  列ヘッダーを含むセルをクリックします。 **LastName**します。  
  
2.  型**姓**2 つの単語の間にスペースをなど、キーを押します**Enter**します。  
  
### <a name="to-save-data"></a>データを保存するには  
  
1.  クリックして**保存**ワークシートにします。  
  
2.  Excel を終了します。 クリックして**いいえ**行った変更を保存するように求められたらします。  
  
3.  キーを押して**F5**プロジェクトをもう一度実行します。  
  
     リスト オブジェクトからのデータが格納、**従業員**テーブル。  
  
4.  注意してセル内の名前**B7**が**Anderson**、行われ、元のデータベースに保存するデータは変更できます。 列ヘッダー **LastName**が、列ヘッダーがデータベースにバインドされていないと、ワークシートに加えた変更を保存しなかったため、スペースを入れずに元の形式に変更されました。  
  
### <a name="to-add-new-rows"></a>新しい行を追加するには  
  
1. リスト オブジェクト内のセルを選択します。  
  
    アスタリスクが付いて、一覧の下部に新しい行が表示されます (* *\\* * *)、新しい行の最初のセルにします。  
  
2. 空の行で、次の情報を追加します。  
  
   |EmployeeID|LastName|FirstName|タイトル|  
   |----------------|--------------|---------------|-----------|  
   |10|Ito|Shu|営業マネージャー|  
  
### <a name="to-delete-rows"></a>行を削除するには  
  
-   ワークシートの左端までの番号 16 (16 行) を右クリックし、**削除**します。  
  
### <a name="to-sort-the-rows-in-the-list"></a>一覧の行を並べ替える  
  
1.  リスト内のセルを選択します。  
  
     各列ヘッダーの矢印ボタンが表示されます。  
  
2.  矢印ボタンをクリックして、**姓**列ヘッダー。  
  
3.  クリックして**昇順で並べ替えます**します。  
  
     行は、姓でアルファベット順に並べ替えられます。  
  
### <a name="to-filter-information"></a>情報をフィルター処理  
  
1.  リスト内のセルを選択します。  
  
2.  矢印ボタンをクリックして、**タイトル**列ヘッダー。  
  
3.  クリックして**営業担当者**します。  
  
     一覧にある行のみが表示**の営業担当者**で、**タイトル**列。  
  
4.  矢印ボタンをクリックして、**タイトル**列ヘッダーをもう一度です。  
  
5.  クリックして **(すべて)** します。  
  
     フィルターが削除され、すべての行が表示されます。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、データベース内のテーブルをリスト オブジェクトにバインドの基本を説明します。 ここでは、次のタスクを行います。  
  
-   データをキャッシュにオフラインで使用できるようにします。 詳細については、「[方法 :オフラインか、サーバーで使用するデータをキャッシュ](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)します。  
  
-   ソリューションをデプロイします。 詳細については、次を参照してください。 [Office ソリューションを配置](../vsto/deploying-an-office-solution.md)します。  
  
-   フィールドとテーブル間のマスター/詳細関係を作成します。 詳細については、「[チュートリアル:キャッシュされたデータセットを使用してマスター/詳細関係を作成して](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [チュートリアル: ドキュメント レベルのプロジェクトでの単純データ バインディング](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
