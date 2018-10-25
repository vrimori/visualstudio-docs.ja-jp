---
title: 'チュートリアル: キャッシュされたデータセットを使用したマスター/詳細関係を作成します。'
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
ms.openlocfilehash: 9d877eae119c922939ea61007a845e5bd7049076
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933158"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>チュートリアル: キャッシュされたデータセットを使用したマスター/詳細関係を作成します。
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
  
-   SQL Server の Northwind サンプル データベースへのアクセス。 データベースには、開発用コンピューター上またはサーバーを指定できます。  
  
-   SQL Server データベースの読み書きアクセス許可。  
  
## <a name="create-a-new-project"></a>新しいプロジェクトを作成する  
 この手順では、Excel ブック プロジェクトを作成します。  
  
### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1. 名前の Excel ブック プロジェクトを作成**マイ マスター/詳細**、Visual Basic または c# を使用します。 必ず**新しい文書を作成**が選択されています。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
   デザイナーで新しい Excel ブックを開き、**マイ Master-detail**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
## <a name="create-the-data-source"></a>データ ソースを作成します。  
 **[データ ソース]** ウィンドウを使用して、型指定されたデータセットをプロジェクトに追加します。  
  
### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1. 場合、**データソース**ウィンドウが表示されない、メニュー バーで 表示することによって、**ビュー** > **その他の Windows**  >  **データ ソース**します。  
  
2. **[新しいデータ ソースの追加]** をクリックして **データ ソース構成ウィザード**を開始します。  
  
3. 選択**データベース**順にクリックします**次**します。  
  
4. Northwind サンプル SQL Server データベースへのデータ接続を選択するかを使用して新しい接続を追加、**新しい接続**ボタンをクリックします。  
  
5. 選択すると、接続を作成したら、 をクリックして**次**します。  
  
6. クリックしてが選択されている場合、接続を保存するオプションをオフに**次**します。  
  
7. 展開、**テーブル**内のノード、**データベース オブジェクト**ウィンドウ。  
  
8. 選択、**注文**テーブルおよび**Order Details**テーブル。  
  
9. **[完了]** をクリックします。  
  
   ウィザードは、2 つのテーブルを追加、**データソース**ウィンドウ。 表示されているプロジェクトに型指定されたデータセットを追加**ソリューション エクスプ ローラー**します。  
  
## <a name="add-controls-to-the-worksheet"></a>ワークシートにコントロールを追加します。  
 この手順では、最初のワークシートに名前付き範囲、リスト オブジェクト、および 2 つのボタンを追加します。 名前付き範囲およびリスト オブジェクトを最初に、追加、**データソース**ウィンドウ、データ ソースに自動的にバインドされているようにします。 次からボタンを追加、**ツールボックス**します。  
  
### <a name="to-add-a-named-range-and-a-list-object"></a>名前付き範囲およびリスト オブジェクトを追加するには  
  
1.  いることを確認、**マイ マスター Detail.xlsx** 、Visual Studio デザイナーで開いているブックで**Sheet1**が表示されます。  
  
2.  開く、**データ ソース**ウィンドウを展開し、**注文**ノード。  
  
3.  選択、 **OrderID**列で、表示されるドロップダウン矢印を順にクリックします。  
  
4.  クリックして**NamedRange**をドラッグし、ドロップダウン一覧で、 **OrderID**セルに列**A2**します。  
  
     A<xref:Microsoft.Office.Tools.Excel.NamedRange>という名前のコントロール`OrderIDNamedRange`セルは**A2**します。 、同時に、<xref:System.Windows.Forms.BindingSource>という名前`OrdersBindingSource`、テーブル アダプターの場合は、および<xref:System.Data.DataSet>インスタンスは、プロジェクトに追加されます。 コントロールにバインドする、<xref:System.Windows.Forms.BindingSource>にさらにバインドされます、<xref:System.Data.DataSet>インスタンス。  
  
5.  過去の下にある列の下へスクロール、**注文**テーブル。 一覧の下部には、 **Order Details** ; テーブルの子であるため、ここでは、**注文**テーブル。 このオプションを選択**Order Details**テーブルと同じレベルでは、1 つない、**注文**テーブル、および、表示されるドロップダウン矢印をクリックします。  
  
6.  クリックして**ListObject**をドラッグし、ドロップダウン一覧で、 **OrderDetails**テーブル セルに**A6**します。  
  
7.  A<xref:Microsoft.Office.Tools.Excel.ListObject>という名前のコントロール**Order_DetailsListObject**セルは**A6**にバインドされていると、<xref:System.Windows.Forms.BindingSource>します。  
  
### <a name="to-add-two-buttons"></a>2 つのボタンを追加するには  
  
1. **コモン コントロール**のタブ、**ツールボックス**、追加、<xref:System.Windows.Forms.Button>コントロールをセル**A3**ワークシートの。  
  
    このボタンの名前は`Button1`します。  
  
2. もう 1 つ追加<xref:System.Windows.Forms.Button>コントロールをセル**B3**ワークシートの。  
  
    このボタンの名前は`Button2`します。  
  
   次に、データセットをドキュメントでキャッシュをマークします。  
  
## <a name="cache-the-dataset"></a>データセットをキャッシュします。  
 パブリック、設定、データセットを作成して、ドキュメントにキャッシュするデータセットをマーク、 **CacheInDocument**プロパティ。  
  
### <a name="to-cache-the-dataset"></a>データセットをキャッシュするには  
  
1. 選択**NorthwindDataSet**コンポーネント トレイにします。  
  
2. **プロパティ**ウィンドウで、変更、**修飾子**プロパティを**パブリック**します。  
  
    データセットは、キャッシュを有効にする前にパブリックである必要があります。  
  
3. 変更、 **CacheInDocument**プロパティを**True**します。  
  
   次の手順では、ボタンにテキストを追加し、c# でイベント ハンドラーをフックするコードを追加します。  
  
## <a name="initialize-the-controls"></a>コントロールを初期化します。  
 ボタン テキストを設定し、中にイベント ハンドラーを追加、<xref:Microsoft.Office.Tools.Excel.Workbook.Startup>イベント。  
  
### <a name="to-initialize-the-data-and-the-controls"></a>データと、コントロールを初期化するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**Sheet1.vb**または**Sheet1.cs**、] をクリックし、**コードの表示**ショートカット メニューの [します。  
  
2.  次のコードを追加、`Sheet1_Startup`ボタンのテキストを設定します。  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  C# の場合のみ、追加ボタンのイベント ハンドラーにイベントをクリックして、`Sheet1_Startup`メソッド。  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="add-code-to-enable-scrolling-through-the-records"></a>レコードのスクロールを有効にするコードを追加します。  
 コードを追加して、<xref:System.Windows.Forms.Control.Click>レコード間を移動するには、各ボタンのイベント ハンドラー。  
  
### <a name="to-scroll-through-the-records"></a>レコードをスクロールするには  
  
1.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Control.Click>のイベント`Button1`、下位レコード間を移動するには、次のコードを追加します。  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Control.Click>のイベント`Button2`レコードに進むには、次のコードを追加します。  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
 これで、想定どおりにデータが表示されることと、ソリューションをオフライン使用できるかどうかを確認するブックをテストできます。  
  
### <a name="to-test-the-data-caching"></a>データ キャッシュをテストするには  
  
1.  **F5**キーを押します。  
  
2.  名前付き範囲およびリスト オブジェクトは、データ ソースからのデータで塗りつぶされていることを確認します。  
  
3.  ボタンをクリックして、一部のレコードをスクロールします。  
  
4.  ブックを保存し、ブックと Visual Studio を閉じます。  
  
5.  データベースへの接続を無効にします。 データベースがサーバー上にある場合は、コンピューターからネットワーク ケーブルを外します。 またはデータベースが開発用コンピューター上にある場合は、SQL Server サービスを停止します。  
  
6.  Excel を開き、開き**マイ マスター Detail.xlsx**から、 *\bin*ディレクトリ (*\My Master-Detail\bin* Visual basic または*\My Master-Detail\bin\デバッグ*(C#))。  
  
7.  切断されている場合、ワークシートは通常どおりことを確認するレコードの一部をスクロールします。  
  
8.  データベースに再接続します。 データベースがサーバー上にある場合に、ネットワークにコンピューターをもう一度接続またはデータベースが開発用コンピューター上にある場合は、SQL Server サービスを開始します。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、ワークシートのマスター/詳細データのリレーションシップを作成して、データセットのキャッシュの基本を説明します。 ここでは、次のタスクを行います。  
  
-   ソリューションをデプロイします。 詳細については、次を参照してください[Office ソリューションのデプロイ。](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [キャッシュ データ](../vsto/caching-data.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  