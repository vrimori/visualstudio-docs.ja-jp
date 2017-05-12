---
title: "チュートリアル : Excel のアクション ペインのコントロールへのデータ連結"
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
  - "操作ウィンドウ [Visual Studio での Office 開発], バインド (コントロールを)"
  - "操作ウィンドウ [Visual Studio での Office 開発], データ バインド"
  - "コントロール [Visual Studio での Office 開発], データ バインド"
  - "データ バインド [Visual Studio での Office 開発], 操作ウィンドウ"
  - "データ バインド [Visual Studio での Office 開発], スマート ドキュメント"
  - "スマート ドキュメント [Visual Studio での Office 開発], データ バインド"
ms.assetid: 106c07bd-e931-4dc5-94dc-ca43900fe09d
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# チュートリアル : Excel のアクション ペインのコントロールへのデータ連結
  このチュートリアルでは、Microsoft Office Excel の操作ウィンドウ内のコントロールに対するデータのバインドについて説明します。  このコントロールは、SQL Server データベースのテーブル間のマスター\/詳細リレーションシップを示します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   ワークシートへのコントロールの追加  
  
-   操作ウィンドウ コントロールの作成  
  
-   操作ウィンドウ コントロールへのデータ バインド Windows フォーム コントロールの追加  
  
-   アプリケーションが開かれたときの操作ウィンドウの表示  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   Northwind SQL Server サンプル データベースがインストールされたサーバーへのアクセス  
  
-   SQL Server データベースの読み込み\/書き込みアクセス許可  
  
## プロジェクトの作成  
 最初に、Excel ワークブック プロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  My Excel Actions Pane という名前の Excel ワークブック プロジェクトを作成します。  ウィザードで、**\[新規ドキュメントの作成\]** をクリックします。  詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     新しい Excel ブックがデザイナーで開き、**My Excel Actions Pane** プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## プロジェクトへの新しいデータ ソースの追加  
  
#### プロジェクトに新しいデータ ソースを追加するには  
  
1.  **\[データ ソース\]** のウィンドウが表示されない場合は、これを、**\[ビュー\]**、**\[その他のウィンドウ\]** を選択する、メニュー バーの **\[データ ソース\]** 表示されます。  
  
2.  **\[データ ソース構成ウィザード\]** を開始するには **\[新しいデータ ソースの追加\]** を選択します。  
  
3.  **\[データベース\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  SQL Server Northwind サンプル データベースへのデータ接続を選択するか、または **\[新しい接続\]** をクリックして新しい接続を追加します。  
  
5.  **\[次へ\]** をクリックします。  
  
6.  接続を保存するオプションがオンになっている場合はオフにし、**\[次へ\]** をクリックします。  
  
7.  **\[データベース オブジェクト\]** ウィンドウの **\[テーブル\]** ノードを展開します。  
  
8.  **\[Suppliers\]** テーブルの横のチェック ボックスをオンにします。  
  
9. **\[Products\]** テーブルを展開し、**\[ProductName\]**、**\[SupplierID\]**、**\[QuantityPerUnit\]**、および **\[UnitPrice\]** を選択します。  
  
10. \[完了\] をクリックします。  
  
 **\[Suppliers\]** テーブルと **\[Products\]** テーブルが **\[データ ソース\]** ウィンドウに追加されます。  さらに、**ソリューション エクスプローラー**に表示されるプロジェクトに、型指定されたデータセットも追加されます。  
  
## ワークシートへのコントロールの追加  
 次に、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールと <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを、最初のワークシートに追加します。  
  
#### NamedRange コントロールおよび ListObject コントロールを追加するには  
  
1.  **\[My Excel Actions Pane.xlsx\]** ブックが Visual Studio のデザイナーで開いていると、表示 `Sheet1` ことを確認します。  
  
2.  **\[データ ソース\]** ウィンドウの **\[Suppliers\]** テーブルを展開します。  
  
3.  **\[会社名\]** ノードのドロップダウン矢印をクリックし、**\[NamedRange\]** をクリックします。  
  
4.  **\[データ ソース\]** ウィンドウから `Sheet1` のセル **A2** へ、**\[会社名\]** をドラッグします。  
  
     `CompanyNameNamedRange` という名前の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールが作成され、セル **A2** に \<CompanyName\> というテキストが表示されます。  同時に、`suppliersBindingSource` という名前の <xref:System.Windows.Forms.BindingSource>、テーブル アダプター、および <xref:System.Data.DataSet> がプロジェクトに追加されます。  コントロールは <xref:System.Windows.Forms.BindingSource> にバインドされ、さらにこれが <xref:System.Data.DataSet> インスタンスにバインドされます。  
  
5.  **\[データ ソース\]** ウィンドウで、**\[Suppliers\]** テーブルの下にある列をスクロール ダウンします。  リストの一番下には、**\[Suppliers\]** テーブルの子である **\[Products\]** テーブルがあります。  **\[Suppliers\]** テーブルと同じレベルにあるものではなく、この **\[Products\]** テーブルを選択し、表示されるドロップダウン矢印をクリックします。  
  
6.  ドロップダウン リストの **\[ListObject\]** をクリックし、**\[Products\]** テーブルを `Sheet1` のセル **A6** にドラッグします。  
  
     `ProductNameListObject` という名前の <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールがセル **A6** に作成されます。  同時に、`productsBindingSource` という名前の <xref:System.Windows.Forms.BindingSource> とテーブル アダプターがプロジェクトに追加されます。  コントロールは <xref:System.Windows.Forms.BindingSource> にバインドされ、さらにこれが <xref:System.Data.DataSet> インスタンスにバインドされます。  
  
7.  C\# の場合のみ、コンポーネント トレイの **\[suppliersBindingSource\]** を選択し、**\[プロパティ\]** ウィンドウで **\[Modifiers\]** プロパティを Internal に変更します。  
  
## 操作ウィンドウへのコントロールの追加  
 次に、コンボ ボックスを含む操作ウィンドウ コントロールが必要です。  
  
#### 操作ウィンドウ コントロールを追加するには  
  
1.  **ソリューション エクスプローラー**で **My Excel Actions Pane** プロジェクトを選択します。  
  
2.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
3.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[操作ウィンドウ コントロール\]** を選択し、**ActionsControl** という名前を指定して、**\[追加\]** をクリックします。  
  
#### データ バインド Windows フォーム コントロールを操作ウィンドウ コントロールに追加するには  
  
1.  **ツールボックス**の **\[コモン コントロール\]** タブから操作ウィンドウ コントロールへ、<xref:System.Windows.Forms.ComboBox> コントロールをドラッグします。  
  
2.  **\[Size\]** プロパティを 171, 21 に変更します。  
  
3.  ユーザー コントロールのサイズをコンボ ボックスと同じ大きさに変更します。  
  
## 操作ウィンドウ コントロールのデータへのバインド  
 ここでは、<xref:System.Windows.Forms.ComboBox> のデータ ソースを、ワークシート上の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールと同じデータ ソースに設定します。  
  
#### コントロールのデータ バインディング プロパティを設定するには  
  
1.  操作ウィンドウ コントロールを右クリックし、**\[コードの表示\]** をクリックします。  
  
2.  操作ウィンドウ コントロールの <xref:System.Windows.Forms.UserControl.Load> イベントに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ActionsControl.vb#1)]  
  
3.  C\# では、`ActionsControl` のイベント ハンドラーを作成する必要があります。  このコードを `ActionsControl` コンストラクターに追加できます。  イベンド ハンドラーの作成方法の詳細については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#2)]  
  
## 操作ウィンドウの表示  
 実行時に操作ウィンドウ コントロールを追加するまで、操作ウィンドウは表示されません。  
  
#### 操作ウィンドウを表示するには  
  
1.  **ソリューション エクスプローラー**で ThisWorkbook.vb または ThisWorkbook.cs を右クリックし、**\[コードの表示\]** をクリックします。  
  
2.  `ThisWorkbook` クラスで、ユーザー コントロールの新しいインスタンスを作成します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#3)]  
  
3.  `ThisWorkbook` の <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> イベント ハンドラーで、コントロールを操作ウィンドウに追加します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#4)]  
  
## アプリケーションのテスト  
 文書をテストして、文書を開いたときに操作ウィンドウが開き、コントロールの間にマスター\/詳細リレーションシップがあることを確認します。  
  
#### 文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  操作ウィンドウが表示されていることを確認します。  
  
3.  リスト ボックスから会社を選択します。  会社名が <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールに表示され、製品の詳細が <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールに表示されることを確認します。  
  
4.  さまざまな会社を選択して、会社名と製品の詳細が適切に変化することを確認します。  
  
## 次の手順  
 次に行う作業は以下のとおりです。  
  
-   Word のコントロールへのデータのバインド。  詳細については、「[チュートリアル : Word の操作ウィンドウ上のコントロールへのデータ バインド](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)」を参照してください。  
  
-   プロジェクトの配置。  詳細については、「[ClickOnce を使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)」を参照してください。  
  
## 参照  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [方法 : アクション ペイン上のコントロールのレイアウトを管理する](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  