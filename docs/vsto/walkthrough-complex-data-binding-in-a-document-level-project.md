---
title: "チュートリアル: ドキュメント レベルのプロジェクトでの複雑なデータ バインディング |Microsoft ドキュメント"
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
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3ee0dc3da505807a572b646c4c286132cc45ca81
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>チュートリアル : ドキュメント レベルのプロジェクトでの複合データ バインディング
  このチュートリアルでは、ドキュメント レベルのプロジェクトでの複合データ バインディングの基本について説明します。 Microsoft Office Excel ワークシートの複数のセルを Northwind SQL Server データベース内のフィールドにバインドできます。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   データ ソースのブック プロジェクトに追加します。  
  
-   データ バインド コントロールをワークシートに追加します。  
  
-   データの変更をデータベースに保存します。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   Northwind SQL Server サンプル データベースを持つサーバーにアクセスします。  
  
-   読み取りと書き込みの SQL Server データベースにアクセスを許可します。  
  
## <a name="creating-a-new-project"></a>新規プロジェクトの作成  
 最初の手順では、Excel ブック プロジェクトを作成します。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Excel ブック プロジェクトを作成**マイの複合データ バインディング**です。 ウィザードで、次のように選択します。**新しいドキュメントを作成する**です。  
  
     詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     デザイナーで新しい Excel ブックを開き、**マイの複合データ バインディング**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="creating-the-data-source"></a>データ ソースの作成  
 **[データ ソース]** ウィンドウを使用して、型指定されたデータセットをプロジェクトに追加します。  
  
#### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1.  **[データ ソース]** ウィンドウが表示されていない場合は、メニュー バーの **[表示]**、 **[その他のウィンドウ]**、 **[データ ソース]**の順にクリックして表示します。  
  
2.  **[新しいデータ ソースの追加]** をクリックして **データ ソース構成ウィザード**を開始します。  
  
3.  選択**データベース** をクリックし、**次**です。  
  
4.  Northwind サンプル SQL Server データベースへのデータ接続を選択するかを使用して新しい接続を追加、**新しい接続**ボタンをクリックします。  
  
5.  接続を選択または作成した後にをクリックして**次**です。  
  
6.  クリックしてオンになっている場合、接続を保存するオプションをオフに**次**です。  
  
7.  展開して、**テーブル**内のノード、**データベース オブジェクト**ウィンドウです。  
  
8.  次のチェック ボックスをオン、**従業員**テーブル。  
  
9. **[完了]**をクリックします。  
  
 ウィザードでは追加、**従業員**テーブル、**データ ソース**ウィンドウです。 表示されているプロジェクトにも型指定されたデータセットを追加**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-controls-to-the-worksheet"></a>ワークシートへのコントロールの追加  
 ワークシートが表示されます、**従業員**表に、ブックを開いたときにします。 データを変更して、データベースに戻すボタンをクリックしてそれらの変更を保存することができます。  
  
 テーブルにワークシートを自動的にバインドするには追加、<xref:Microsoft.Office.Tools.Excel.ListObject>からワークシートにコントロール、**データソース**ウィンドウです。 ユーザーに提供する、変更を保存するオプションを追加、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**です。  
  
#### <a name="to-add-a-list-object"></a>リスト オブジェクトを追加するには  
  
1.  いることを確認、**マイの複雑なデータ Binding.xlsx** 、Visual Studio デザイナーで開いているブックで**Sheet1**が表示されます。  
  
2.  開く、**データソース**ウィンドウを選択、**従業員**ノード。  
  
3.  表示されるドロップダウン矢印をクリックします。  
  
4.  選択**ListObject**ドロップダウン リストでします。  
  
5.  ドラッグ、**従業員**テーブル セルに**A6**です。  
  
     A<xref:Microsoft.Office.Tools.Excel.ListObject>という名前のコントロール`EmployeesListObject`セルで作成された**A6**です。 同時に、<xref:System.Windows.Forms.BindingSource>という名前`EmployeesBindingSource`、テーブルのアダプターでは、および<xref:System.Data.DataSet>インスタンスは、プロジェクトに追加されます。 コントロールがバインドされている、 <xref:System.Windows.Forms.BindingSource>、さらにこれがバインドに、<xref:System.Data.DataSet>インスタンス。  
  
#### <a name="to-add-a-button"></a>ボタンを追加するには  
  
1.  **コモン コントロール**のタブ、**ツールボックス**、追加、<xref:System.Windows.Forms.Button>コントロールをセル**A4**ワークシートのです。  
  
 次の手順では、ワークシートが開いたら、ボタンにテキストを追加します。  
  
## <a name="initializing-the-control"></a>コントロールの初期化  
 テキストのボタンを追加、<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>イベント ハンドラー。  
  
#### <a name="to-initialize-the-control"></a>コントロールを初期化するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**Sheet1.vb**または**Sheet1.cs**、クリックして**コードの表示**ショートカット メニューの します。  
  
2.  次のコードを追加、 `Sheet1_Startup` b のテキストを設定するメソッドを`utton`です。  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]  
  
3.  C# の場合のみ、追加のイベント ハンドラー、<xref:System.Windows.Forms.Control.Click>イベントを`Sheet1_Startup`メソッドです。  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]  
  
 今すぐ処理するコードを追加、<xref:System.Windows.Forms.Control.Click>ボタンのイベントです。  
  
## <a name="saving-changes-to-the-database"></a>データベースに変更を保存  
 すべての変更が加えられたデータベースに明示的に保存されるまでに、データがローカルのデータセットにのみ存在します。  
  
#### <a name="to-save-changes-to-the-database"></a>データベースに変更を保存するには  
  
1.  イベント ハンドラーを追加、 <xref:System.Windows.Forms.Control.Click> b のイベント`utton`データセット内のデータベースに加えられたすべての変更をコミットする次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 これで、データが、想定どおりに表示されると、リスト オブジェクト内のデータを操作できることを確認するブックをテストできます。  
  
#### <a name="to-test-the-data-binding"></a>データ バインドをテストするには  
  
-   F5 キーを押します。  
  
     ブックを開いたときに、リスト オブジェクトがからデータを入力することを確認、**従業員**テーブル。  
  
#### <a name="to-modify-data"></a>データを変更するには  
  
1.  セルをクリックして**B7**、名が含まれている必要があります**春**です。  
  
2.  名前を入力します**Anderson**、ENTER キーを押します。  
  
#### <a name="to-modify-a-column-header"></a>列ヘッダーを変更するには  
  
1.  列ヘッダーを含むセルをクリックして**LastName**です。  
  
2.  型**姓**2 つの単語の間にスペースをなど、ENTER キーを押します。  
  
#### <a name="to-save-data"></a>データを保存するには  
  
1.  をクリックして**保存**ワークシートにします。  
  
2.  Excel を終了します。 をクリックして**いいえ**加えた変更を保存するように求められたらです。  
  
3.  F5 キーを押してプロジェクトを再度実行します。  
  
     リスト オブジェクトはからデータを格納、**従業員**テーブル。  
  
4.  注意してセル内の名前**B7**が**Anderson**、作成して、データベースに保存するデータは変更できます。 列ヘッダー **LastName**が、列ヘッダーがデータベースにバインドされていないと、ワークシートに加えた変更を保存しなかったため、スペースを入れずに元の形式に変更されました。  
  
#### <a name="to-add-new-rows"></a>新しい行を追加するには  
  
1.  リスト オブジェクト内のセルを選択します。  
  
     アスタリスクで、一覧の下部にある新しい行が表示されます (**\***)、新しい行の最初のセルにします。  
  
2.  空の行で、次の情報を追加します。  
  
    |EmployeeID|LastName|FirstName|タイトル|  
    |----------------|--------------|---------------|-----------|  
    |10|Ito|Shu|販売責任者|  
  
#### <a name="to-delete-rows"></a>行を削除するには  
  
-   ワークシートの一番左にある数 16 (16 行) を右クリックし、をクリックして**削除**です。  
  
#### <a name="to-sort-the-rows-in-the-list"></a>リスト内の行を並べ替える  
  
1.  リスト内のセルを選択します。  
  
     各列見出しの矢印ボタンが表示されます。  
  
2.  ある矢印ボタンをクリックして、**姓**列ヘッダー。  
  
3.  をクリックして**昇順で並べ替え**です。  
  
     行は、最後の名前でアルファベット順に並べ替えられます。  
  
#### <a name="to-filter-information"></a>情報をフィルター処理  
  
1.  リスト内のセルを選択します。  
  
2.  ある矢印ボタンをクリックして、**タイトル**列ヘッダー。  
  
3.  をクリックして**営業担当者**です。  
  
     一覧を持つ行のみを表示する**販売担当者**で、**タイトル**列です。  
  
4.  ある矢印ボタンをクリックして、**タイトル**列ヘッダーをもう一度です。  
  
5.  をクリックして**(すべて)**です。  
  
     フィルターが削除され、すべての行が表示されます。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、リスト オブジェクトへのデータベースのテーブルのバインドの基礎を説明します。 ここでは、次のタスクを行います。  
  
-   オフライン使用できるようにする、データをキャッシュします。 詳細については、次を参照してください。[する方法: オフラインで使用またはサーバー上にデータをキャッシュ](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)です。  
  
-   ソリューションを展開します。 詳細については、次を参照してください。 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)です。  
  
-   フィールドとテーブル間のマスター/詳細関係を作成します。 詳細については、次を参照してください。[チュートリアル: データセットを作成するマスターの詳細関係を使用して、キャッシュ](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)です。  
  
## <a name="see-also"></a>参照  
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [チュートリアル: ドキュメント レベルのプロジェクトでの単純データ バインディング](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  