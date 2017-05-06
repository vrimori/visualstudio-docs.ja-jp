---
title: "チュートリアル : キャッシュされたデータセットを使用したマスター/詳細関係の作成"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "データ キャッシュ [Visual Studio での Office 開発], マスター/詳細リレーションシップ"
  - "マスター/詳細テーブル [Visual Studio での Office 開発], チュートリアル"
ms.assetid: 419f4e07-c67f-4fc9-973a-bc794f349ac3
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# チュートリアル : キャッシュされたデータセットを使用したマスター/詳細関係の作成
  このチュートリアルでは、ワークシート上でのマスター\/詳細リレーションシップの作成、およびソリューションをオフラインで使用することを目的とするデータのキャッシュについて説明します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   ワークシートにコントロールを追加します。  
  
-   ワークシートにキャッシュするデータセットを設定する。  
  
-   レコード間をスクロールするためのコードを追加する。  
  
-   プロジェクトのテスト  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   Northwind SQL Server サンプル データベースへのアクセス。  このデータベースは開発用コンピューターまたはサーバーにあります。  
  
-   SQL Server データベースの読み込み\/書き込みアクセス許可  
  
## 新規プロジェクトの作成  
 この手順では、Excel ブックのプロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  Visual Basic または C\# を使用して、**My Master\-Detail** という名前の Excel ブック プロジェクトを作成します。  **\[新規ドキュメントの作成\]** が選択されていることを確認します。  詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
 新しい Excel ブックがデザイナーで開き、My Master\-Detail プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## データ ソースの作成  
 **\[データ ソース\]** ウィンドウを使用して型指定されたデータセットをプロジェクトに追加します。  
  
#### データ ソースを作成するには  
  
1.  **\[データ ソース\]** のウィンドウが表示されない場合は、これを、**\[ビュー\]**、**\[その他のウィンドウ\]** を選択する、メニュー バーの **\[データ ソース\]** 表示されます。  
  
2.  **\[データ ソース構成ウィザード\]** を開始するには **\[新しいデータ ソースの追加\]** を選択します。  
  
3.  **\[データベース\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  SQL Server Northwind サンプル データベースへのデータ接続を選択するか、または **\[新しい接続\]** をクリックして新しい接続を追加します。  
  
5.  接続を選択または作成したら、**\[次へ\]** をクリックします。  
  
6.  接続を保存するオプションがオンになっている場合はオフにし、**\[次へ\]** をクリックします。  
  
7.  **\[データベース オブジェクト\]** ウィンドウの **\[テーブル\]** ノードを展開します。  
  
8.  **\[Orders\]** テーブルと **\[Order Details\]** テーブルを選択します。  
  
9. \[完了\] をクリックします。  
  
 **\[データ ソース\]** ウィンドウに 2 つのテーブルが追加されます。  さらに、**ソリューション エクスプローラー**に表示されるプロジェクトに、型指定されたデータセットも追加されます。  
  
## ワークシートへのコントロールの追加  
 この手順では、1 番目のワークシートに、名前付き範囲、リスト オブジェクト、および 2 つのボタンを追加します。  最初に、自動的にデータ ソースにバインドされるように、**\[データ ソース\]** ウィンドウから名前付き範囲とリスト オブジェクトを追加します。  次に、**ツールボックス**からボタンを追加します。  
  
#### 名前付き範囲とリスト オブジェクトを追加するには  
  
1.  **\[My Master\-Detail.xlsx\]** ブックが Visual Studio のデザイナーで開いていると、表示 **\[Sheet1\]** ことを確認します。  
  
2.  **\[データ ソース\]** ウィンドウを表示し、**\[Orders\]** ノードを展開します。  
  
3.  **\[OrderID\]** 列を選択し、表示されるドロップダウン矢印をクリックします。  
  
4.  ドロップダウン リストの **\[NamedRange\]** をクリックし、**\[OrderID\]** 列をセル **A2** にドラッグします。  
  
     `OrderIDNamedRange` という名前の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールがセル **A2** に作成されます。  同時に、`OrdersBindingSource` という名前の <xref:System.Windows.Forms.BindingSource>、テーブル アダプター、および <xref:System.Data.DataSet> のインスタンスがプロジェクトに追加されます。  コントロールは <xref:System.Windows.Forms.BindingSource> にバインドされ、さらにこれが <xref:System.Data.DataSet> インスタンスにバインドされます。  
  
5.  **\[Orders\]** テーブルの下にある列をスクロール ダウンします。  リストの一番下には、**Orders** テーブルの子である **Order Details** テーブルがあります。  **Orders** テーブルと同じレベルにあるテーブルではなく、この **\[Order Details\]** テーブルを選択し、表示されるドロップダウン矢印をクリックします。  
  
6.  ドロップダウン リストの **\[ListObject\]** をクリックし、**\[Order Details\]** テーブルをセル **A6** にドラッグします。  
  
7.  **Order\_DetailsListObject** という名前の <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールがセル **A6** に作成され、<xref:System.Windows.Forms.BindingSource> にバインドされます。  
  
#### 2 つのボタンを追加するには  
  
1.  **ツールボックス**の **\[コモン コントロール\]** タブからワークシートのセル **A3** へ、<xref:System.Windows.Forms.Button> コントロールをドラッグします。  
  
     このボタンは `Button1` という名前になります。  
  
2.  別の <xref:System.Windows.Forms.Button> コントロールを、ワークシートのセル **B3** に追加します。  
  
     このボタンは `Button2` という名前になります。  
  
 次に、文書にキャッシュされるデータセットをマーキングします。  
  
## データセットのキャッシュ  
 データセットをパブリックにし、**CacheInDocument** プロパティを設定することによって、文書にキャッシュするデータセットをマーキングします。  
  
#### データセットをキャッシュするには  
  
1.  コンポーネント トレイの **\[NorthwindDataSet\]** を選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、**Modifiers** プロパティを **Public** に設定します。  
  
     キャッシュを有効にする前に、データセットをパブリックにする必要があります。  
  
3.  **CacheInDocument** プロパティを **True** に変更します。  
  
 次の手順では、ボタンにテキストを追加し、C\# でイベント ハンドラーをフックするコードを追加します。  
  
## コントロールの初期化  
 ボタンのテキストを設定し、<xref:Microsoft.Office.Tools.Excel.Workbook.Startup> イベント時のイベント ハンドラーを追加します。  
  
#### データとコントロールを初期化するには  
  
1.  **ソリューション エクスプローラー**の **Sheet1.vb** または **Sheet1.cs** を右クリックし、ショートカット メニューの **\[コードの表示\]** をクリックします。  
  
2.  `Sheet1_Startup` メソッドに次のコードを追加して、ボタンのテキストを設定します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#15)]
     [!code-vb[Trin_VstcoreDataExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#15)]  
  
3.  C\# の場合のみ、ボタン クリック イベントのイベント ハンドラーを `Sheet1_Startup` メソッドに追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#16)]  
  
## レコード間をスクロールするためのコードの追加  
 レコード間を移動するためのコードを各ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに追加します。  
  
#### レコード間をスクロールするには  
  
1.  `Button1` の <xref:System.Windows.Forms.Control.Click> イベントのイベント ハンドラーを追加し、レコード間を後方に移動できるように次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#17)]
     [!code-vb[Trin_VstcoreDataExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#17)]  
  
2.  `Button2` の <xref:System.Windows.Forms.Control.Click> イベントのイベント ハンドラーを追加し、レコード間を前方に移動できるように次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#18)]
     [!code-vb[Trin_VstcoreDataExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#18)]  
  
## アプリケーションのテスト  
 ブックをテストして、データが期待どおりに表示され、ソリューションをオフラインで使用できることを確認します。  
  
#### データ キャッシュをテストするには  
  
1.  **F5** キーを押します。  
  
2.  名前付き範囲とリスト オブジェクトに、データ ソースのデータが設定されていることを確認します。  
  
3.  ボタンをクリックして、いくつかのレコードをスクロールします。  
  
4.  ブックを保存し、ブックと Visual Studio を閉じます。  
  
5.  データベースへの接続を無効にします。  データベースがサーバー上にある場合はコンピューターからネットワーク ケーブルを外します。また、データベースが開発用コンピューター上にある場合は SQL Server サービスを停止します。  
  
6.  開いている Excel は、を\\bin のディレクトリ \(Visual Basic の\\My Master\-Detail\\bin または、C の\\My Master\-Detail\\bin\\debug\) の **\[My Master\-Detail.xlsx\]** を開きます。  
  
7.  いくつかのレコードをスクロールして、接続していない状態で、ワークシートが正常に動作することを確認します。  
  
8.  データベースに再接続します。  データベースがサーバー上にある場合はコンピューターをネットワークに再接続します。また、データベースが開発用コンピューター上にある場合は SQL Server サービスを開始します。  
  
## 次の手順  
 このチュートリアルでは、ワークシート上でのマスター\/詳細リレーションシップの作成、およびデータセットのキャッシュの基本事項について説明します。  次に行う作業は以下のとおりです。  
  
-   ソリューションの配置。  詳細については、「[Office ソリューションの配置](../vsto/deploying-an-office-solution.md)」を参照してください。  
  
## 参照  
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [キャッシュされたデータ](../vsto/caching-data.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  