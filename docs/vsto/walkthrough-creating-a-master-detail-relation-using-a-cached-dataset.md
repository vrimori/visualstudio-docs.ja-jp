---
title: 'チュートリアル: キャッシュされたデータセットを使用してマスターの詳細関係の作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: abe0b766214c1906afcf443c23948c492a6bde90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-master-detail-relation-using-a-cached-dataset"></a>チュートリアル: キャッシュされたデータセットを使用してマスターの詳細関係の作成
  このチュートリアルでは、ワークシートで、マスター/詳細関係を作成して、ソリューションをオフラインで使用できるように、データのキャッシュを示します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   コントロールをワークシートに追加します。  
  
-   ワークシート内でキャッシュされるデータセットを設定します。  
  
-   レコードのスクロールを有効にするコードを追加します。  
  
-   プロジェクトをテストします。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   Northwind SQL Server サンプル データベースにアクセスします。 データベースには、開発用コンピューター上またはサーバーを指定できます。  
  
-   読み取りと書き込みの SQL Server データベースにアクセスを許可します。  
  
## <a name="creating-a-new-project"></a>新規プロジェクトの作成  
 このステップでは、Excel ブック プロジェクトを作成します。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Excel ブック プロジェクトを作成**マイ マスター/詳細**、Visual Basic または c# を使用します。 確認して**新しいドキュメントを作成する**が選択されています。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
 デザイナーで新しい Excel ブックを開き、**マイ マスター/詳細**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="creating-the-data-source"></a>データ ソースの作成  
 **[データ ソース]** ウィンドウを使用して、型指定されたデータセットをプロジェクトに追加します。  
  
#### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1.  **[データ ソース]** ウィンドウが表示されていない場合は、メニュー バーの **[表示]**、 **[その他のウィンドウ]**、 **[データ ソース]**の順にクリックして表示します。  
  
2.  **[新しいデータ ソースの追加]** をクリックして **データ ソース構成ウィザード**を開始します。  
  
3.  選択**データベース** をクリックし、**次**です。  
  
4.  Northwind サンプル SQL Server データベースへのデータ接続を選択するかを使用して新しい接続を追加、**新しい接続**ボタンをクリックします。  
  
5.  選択するか、接続を作成するをクリックして**次**です。  
  
6.  クリックしてオンになっている場合、接続を保存するオプションをオフに**次**です。  
  
7.  展開して、**テーブル**内のノード、**データベース オブジェクト**ウィンドウです。  
  
8.  選択、 **Orders**テーブルおよび**Order Details**テーブル。  
  
9. **[完了]**をクリックします。  
  
 ウィザードは、2 つのテーブルを追加、**データソース**ウィンドウです。 表示されているプロジェクトにも型指定されたデータセットを追加**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-controls-to-the-worksheet"></a>ワークシートへのコントロールの追加  
 この手順では、最初のワークシートに、名前付き範囲、リスト オブジェクト、および 2 つのボタンを追加します。 最初に、名前付き範囲とオブジェクトを追加、一覧から、**データ ソース**ウィンドウに自動的にデータ ソースにバインドされるようにします。 次に、追加のボタン、**ツールボックス**です。  
  
#### <a name="to-add-a-named-range-and-a-list-object"></a>名前付き範囲およびリスト オブジェクトを追加するには  
  
1.  いることを確認、**マイ マスター Detail.xlsx** 、Visual Studio デザイナーで開いているブックで**Sheet1**が表示されます。  
  
2.  開く、**データ ソース**ウィンドウを展開し、 **Orders**ノード。  
  
3.  選択、 **OrderID**列で、表示されるドロップダウン矢印をクリックします。  
  
4.  をクリックして**NamedRange**をドラッグし、ドロップダウン一覧で、 **OrderID**セルに列**A2**です。  
  
     A<xref:Microsoft.Office.Tools.Excel.NamedRange>という名前のコントロール`OrderIDNamedRange`セルで作成された**A2**です。 同時に、<xref:System.Windows.Forms.BindingSource>という名前`OrdersBindingSource`、テーブルのアダプターでは、および<xref:System.Data.DataSet>インスタンスは、プロジェクトに追加されます。 コントロールがバインドされている、 <xref:System.Windows.Forms.BindingSource>、さらにこれがバインドに、<xref:System.Data.DataSet>インスタンス。  
  
5.  過去の下にある列を下にスクロール、 **Orders**テーブル。 一覧の下部には、 **Order Details**テーブルです。 ここでは、の子になっているため、 **Orders**テーブル。 このオプションを選択**Order Details**テーブルと同じレベルにあるものではなく、 **Orders**テーブル、および、表示されるドロップダウン矢印をクリックします。  
  
6.  をクリックして**ListObject**をドラッグし、ドロップダウン一覧で、 **OrderDetails**テーブル セルに**A6**です。  
  
7.  A<xref:Microsoft.Office.Tools.Excel.ListObject>という名前のコントロール**Order_DetailsListObject**セルで作成された**A6**にバインドされていると、<xref:System.Windows.Forms.BindingSource>です。  
  
#### <a name="to-add-two-buttons"></a>2 つのボタンを追加するには  
  
1.  **コモン コントロール**のタブ、**ツールボックス**、追加、<xref:System.Windows.Forms.Button>コントロールをセル**A3**ワークシートのです。  
  
     このボタンの名前は`Button1`します。  
  
2.  もう 1 つ追加<xref:System.Windows.Forms.Button>コントロールをセル**B3**ワークシートのです。  
  
     このボタンの名前は`Button2`します。  
  
 次に、ドキュメントでキャッシュされるデータセットをマークします。  
  
## <a name="caching-the-dataset"></a>データセットのキャッシュ  
 データセットをパブリック、設定は、データセットをすることで、ドキュメントでキャッシュをマーク、 **CacheInDocument**プロパティです。  
  
#### <a name="to-cache-the-dataset"></a>データセットをキャッシュするには  
  
1.  選択**NorthwindDataSet**コンポーネント トレイにします。  
  
2.  **プロパティ**ウィンドウで、変更、**修飾子**プロパティを**パブリック**です。  
  
     キャッシュを有効にする前に、データセットはパブリックである必要があります。  
  
3.  変更、 **CacheInDocument**プロパティを**True**です。  
  
 次の手順では、ボタンにテキストを追加し、C# の場合、イベント ハンドラーをフックするコードを追加します。  
  
## <a name="initializing-the-controls"></a>コントロールの初期化  
 ボタンのテキストを設定中にイベント ハンドラーを追加して、<xref:Microsoft.Office.Tools.Excel.Workbook.Startup>イベント。  
  
#### <a name="to-initialize-the-data-and-the-controls"></a>データと、コントロールを初期化するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**Sheet1.vb**または**Sheet1.cs**、クリックして**コードの表示**ショートカット メニューの します。  
  
2.  次のコードを追加、`Sheet1_Startup`ボタンのテキストを設定します。  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  C# の場合のみ、追加、ボタンのイベント ハンドラーにイベントをクリックして、`Sheet1_Startup`メソッドです。  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>レコードのスクロールを有効にするコードを追加します。  
 コードを追加して、<xref:System.Windows.Forms.Control.Click>レコード間を移動するには、各ボタンのイベント ハンドラー。  
  
#### <a name="to-scroll-through-the-records"></a>レコードをスクロールするには  
  
1.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Control.Click>のイベント`Button1`レコードを前後に移動するには、次のコードを追加します。  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Control.Click>のイベント`Button2`レコードに進むには、次のコードを追加します。  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 これで、想定どおりにデータが表示されると、ソリューションをオフライン使用できるかどうかを確認するブックをテストできます。  
  
#### <a name="to-test-the-data-caching"></a>データ キャッシュをテストするには  
  
1.  **F5**キーを押します。  
  
2.  名前付き範囲およびリスト オブジェクトで塗りつぶされて、データ ソースからデータを確認します。  
  
3.  ボタンをクリックして、レコードの一部をスクロールします。  
  
4.  ブックを保存し、ブックと Visual Studio を閉じます。  
  
5.  データベースへの接続を無効にします。 サーバーでは、データベースがある場合は、コンピューターからネットワーク ケーブルを外します。 またはデータベースが開発用コンピューター上にある場合は、SQL Server サービスを停止します。  
  
6.  Excel を開き**マイ マスター Detail.xlsx** \bin ディレクトリ (Visual Basic で \My Master-Detail\bin または c# で \My Master-Detail\bin\debug) からです。  
  
7.  切断されている場合、ワークシートが通常どおり動作するを表示するレコードの一部をスクロールします。  
  
8.  データベースに再接続します。 サーバーでは、データベースがある場合に、ネットワークにコンピューターをもう一度接続またはデータベースが開発用コンピューター上にある場合は、SQL Server サービスを開始します。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、ワークシートにマスター/詳細形式のデータ リレーションシップを作成して、データセットのキャッシュの基礎を説明します。 ここでは、次のタスクを行います。  
  
-   ソリューションを展開します。 詳細については、次を参照してください[Office ソリューションの配置。](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [データのキャッシュ](../vsto/caching-data.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  