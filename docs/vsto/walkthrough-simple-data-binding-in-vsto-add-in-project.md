---
title: "チュートリアル: VSTO アドイン プロジェクトでの単純データ バインディング | Microsoft Docs"
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
  - "データ [Visual Studio での Office 開発]、バインド (データを)"
  - "データ バインディング [Visual Studio での Office 開発]、Word"
  - "データ [Visual Studio での Office 開発]、単純バインド (データを)"
ms.assetid: b248d194-a8b1-4f87-94c4-24e940eea1fd
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# チュートリアル: VSTO アドイン プロジェクトでの単純データ バインディング
  VSTO アドイン プロジェクトでは、ホスト コントロールと Windows フォーム コントロールにデータをバインドできます。 このチュートリアルでは、実行時に Microsoft Office Word 文書にコントロールを追加して、そのコントロールをデータにバインドする方法を示します。  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   実行時にドキュメントに <xref:Microsoft.Office.Tools.Word.ContentControl> を追加する。  
  
-   コントロールをデータセットのインスタンスに接続する <xref:System.Windows.Forms.BindingSource> を作成する。  
  
-   ユーザーがレコードをスクロールしてレコードをコントロールに表示できるようにする。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
-   `AdventureWorksLT` サンプル データベースがアタッチされた SQL Server 2005 または SQL Server 2005 Express の実行中のインスタンスへのアクセス。`AdventureWorksLT` データベースは、[CodePlex の Web サイト](http://go.microsoft.com/fwlink/?LinkId=115611)からダウンロードできます。 データベースをアタッチする方法について詳しくは、次のトピックをご覧ください。  
  
    -   SQL Server Management Studio または SQL Server Management Studio Express を使用してデータベースをアタッチする場合は、「[データベースをアタッチする方法 \(SQL Server Management Studio\)](http://msdn.microsoft.com/ja-jp/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa)」をご覧ください。  
  
    -   コマンド ラインを使用してデータベースをアタッチする場合は、「[データベース ファイルを SQL Server Express にアタッチする方法](http://msdn.microsoft.com/ja-jp/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68)」をご覧ください。  
  
## 新規プロジェクトの作成  
 まず、Word VSTO アドイン プロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  Visual Basic または C\# を使用して、**Populating Documents from a Database** という名前の Word VSTO アドイン プロジェクトを作成します。  
  
     詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     Visual Studio により、ThisAddIn.vb ファイルまたは ThisAddIn.cs ファイルが開かれ、**Populating Documents from a Database** プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
2.  プロジェクトのターゲットが [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] である場合、Microsoft.Office.Tools.Word.v4.0.Utilities.dll アセンブリへの参照を追加します。 この参照は、このチュートリアルの後半でプログラムを使用して Windows フォーム コントロールをドキュメントに追加するのに必要です。  
  
## データ ソースの作成  
 **\[データ ソース\]** ウィンドウを使用して、型指定されたデータセットをプロジェクトに追加します。  
  
#### 型指定されたデータセットをプロジェクトに追加するには  
  
1.  **\[データ ソース\]** ウィンドウが表示されていない場合は、メニュー バーの **\[表示\]**、**\[その他のウィンドウ\]**、**\[データ ソース\]** の順にクリックして表示します。  
  
2.  **\[新しいデータ ソースの追加\]** をクリックして**データ ソース構成ウィザード**を開始します。  
  
3.  **\[データベース\]** をクリックして、**\[次へ\]** をクリックします。  
  
4.  `AdventureWorksLT` データベースへの既存の接続がある場合は、その接続を選んで **\[次へ\]** をクリックします。  
  
     それ以外の場合は、**\[新しい接続\]** をクリックし、**\[接続の追加\]** ダイアログ ボックスを使用して新しい接続を作成します。 詳細については、「[方法 : データベース内のデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)」を参照してください。  
  
5.  **\[アプリケーション構成ファイルへの接続文字列を保存\]** ページで、**\[次へ\]** をクリックします。  
  
6.  **\[データベース オブジェクトの選択\]** ページで、**\[テーブル\]** を展開し、**\[Customer \(SalesLT\)\]** を選びます。  
  
7.  **\[完了\]** をクリックします。  
  
     AdventureWorksLTDataSet.xsd ファイルが**ソリューション エクスプローラー**に追加されます。 このファイルでは、次の項目を定義します。  
  
    -   `AdventureWorksLTDataSet` という名前の型指定されたデータセット。 このデータセットは、AdventureWorksLT データベースの **Customer \(SalesLT\)** テーブルの内容を表します。  
  
    -   TableAdapter という名前の `CustomerTableAdapter`。 この TableAdapter は、`AdventureWorksLTDataSet` のデータを読み書きするために使用します。 詳細については、「[TableAdapter の概要](/visual-studio/data-tools/tableadapter-overview)」を参照してください。  
  
     これらのオブジェクトは、どちらもこのチュートリアルの後半で使用します。  
  
## コントロールの作成とデータへのコントロールのバインド  
 このチュートリアルでデータベース レコードを表示するために使用するインターフェイスはごく基本的なもので、ドキュメント内の右側に作成されます。 1 つの <xref:Microsoft.Office.Tools.Word.ContentControl> には一度に 1 つのデータベース レコードが表示されます。2 つの <xref:Microsoft.Office.Tools.Word.Controls.Button> コントロールを使用してレコードを前後にスクロールできます。 コンテンツ コントロールは <xref:System.Windows.Forms.BindingSource> を使用して、データベースに接続します。  
  
 コントロールのデータへのバインドについて詳しくは、「[Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)」をご覧ください。  
  
#### ドキュメントでインターフェイスを作成するには  
  
1.  `ThisAddIn` クラスで、次のコントロールを宣言し、`AdventureWorksLTDataSet` データベースの `Customer` テーブルをスクロールして表示できるようにします。  
  
     [!code-csharp[Trin_WordAddInDatabase#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDatabase#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#1)]  
  
2.  `ThisAddIn_Startup` メソッドに次のコードを追加し、データセットを初期化して、そのデータセットに `AdventureWorksLTDataSet` データベースから得た情報を設定します。  
  
     [!code-csharp[Trin_WordAddInDatabase#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDatabase#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#2)]  
  
3.  `ThisAddIn_Startup` メソッドに次のコードを追加します。 これによりホスト項目が生成され、ドキュメントの機能が拡張されます。 詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
     [!code-csharp[Trin_WordAddInDatabase#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDatabase#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#3)]  
  
4.  ドキュメントの先頭でいくつかの範囲を定義します。 これらの範囲は、テキストを挿入し、コントロールを配置する場所を指定します。  
  
     [!code-csharp[Trin_WordAddInDatabase#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddInDatabase#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#4)]  
  
5.  以前に定義された範囲にインターフェイス コントロールを追加します。  
  
     [!code-csharp[Trin_WordAddInDatabase#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddInDatabase#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#5)]  
  
6.  <xref:System.Windows.Forms.BindingSource> を使用してコンテンツ コントロールを `AdventureWorksLTDataSet` にバインドします。 C\# 開発者の場合、2 つのイベント ハンドラーを <xref:Microsoft.Office.Tools.Word.Controls.Button> コントロールに追加します。  
  
     [!code-csharp[Trin_WordAddInDatabase#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddInDatabase#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#6)]  
  
7.  データベース レコード間を移動するには、次のコードを追加します。  
  
     [!code-csharp[Trin_WordAddInDatabase#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_WordAddInDatabase#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#7)]  
  
## アドインのテスト  
 Word を開くと、コンテンツ コントロールに `AdventureWorksLTDataSet` データセットからのデータが表示されます。**\[次へ\]** と **\[前へ\]** ボタンをクリックして、データベース レコードをスクロールします。  
  
#### VSTO アドインをテストするには  
  
1.  **F5** キーを押します。  
  
     `customerContentControl` という名前のコンテンツ コントロールが作成され、データが読み込まれます。 同時に、`adventureWorksLTDataSet` という名前のデータセット オブジェクトと、`customerBindingSource` という名前の <xref:System.Windows.Forms.BindingSource> がプロジェクトに追加されます。<xref:Microsoft.Office.Tools.Word.ContentControl> が <xref:System.Windows.Forms.BindingSource> にバインドされ、さらにこれがデータセット オブジェクトにバインドされます。  
  
2.  **\[次へ\]** ボタンと **\[前へ\]** ボタンをクリックして、データベース レコードをスクロールします。  
  
## 参照  
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [方法 : データベースのデータをワークシートに読み込む](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [方法 : データベースからドキュメントにデータを読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [方法 : サービスのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [方法 : オブジェクトのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [方法 : ワークシート内でデータベースのレコードをスクロールする](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [方法 : ホスト コントロールからのデータでデータ ソースを更新する](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [チュートリアル : ドキュメント レベルのプロジェクトでの単純データ バインド](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)   
 [チュートリアル : ドキュメント レベルのプロジェクトでの複合データ バインド](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)   
 [Office ソリューションにおけるローカル データベース使用の概要](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [方法 : オブジェクトのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [方法 : ホスト コントロールからのデータでデータ ソースを更新する](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Office ソリューションにおけるローカル データベース使用の概要](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Windows フォーム アプリケーションでのデータへの接続](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource コンポーネントの概要](../Topic/BindingSource%20Component%20Overview.md)  
  
  