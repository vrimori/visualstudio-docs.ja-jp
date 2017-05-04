---
title: "チュートリアル : VSTO アドイン プロジェクトでの複合データ バインディング | Microsoft Docs"
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
  - "データ バインディング [Visual Studio での Office 開発]、Excel"
  - "データ [Visual Studio での Office 開発]、バインド (データを)"
  - "複合データ [Visual Studio での Office 開発]"
ms.assetid: ff52fb56-1f67-4ae2-a3d1-93038619d4e6
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# チュートリアル : VSTO アドイン プロジェクトでの複合データ バインディング
  VSTO アドイン プロジェクトでは、ホスト コントロールと Windows フォーム コントロールにデータをバインドできます。 このチュートリアルでは、Microsoft Office Excel ワークシートにコントロールを追加して、そのコントロールを実行時にデータにバインドする方法を示します。  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   実行時に <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをワークシートに追加する。  
  
-   コントロールをデータセットのインスタンスに接続する <xref:System.Windows.Forms.BindingSource> を作成する。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   `AdventureWorksLT` サンプル データベースがアタッチされた SQL Server 2005 または SQL Server 2005 Express の実行中のインスタンスへのアクセス。`AdventureWorksLT` データベースは、[CodePlex の Web サイト](http://go.microsoft.com/fwlink/?LinkId=115611)からダウンロードできます。 データベースをアタッチする方法について詳しくは、次のトピックをご覧ください。  
  
    -   SQL Server Management Studio または SQL Server Management Studio Express を使用してデータベースをアタッチする場合は、「[データベースをアタッチする方法 \(SQL Server Management Studio\)](http://msdn.microsoft.com/ja-jp/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa)」をご覧ください。  
  
    -   コマンド ラインを使用してデータベースをアタッチする場合は、「[データベース ファイルを SQL Server Express にアタッチする方法](http://msdn.microsoft.com/ja-jp/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68)」をご覧ください。  
  
## 新規プロジェクトの作成  
 まず、Excel VSTO アドイン プロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  Visual Basic または C\# を使用して、**Populating Worksheets from a Database** という名前の Excel VSTO アドイン プロジェクトを作成します。  
  
     詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     Visual Studio により、`ThisAddIn.vb` ファイルまたは `ThisAddIn.cs` ファイルが開かれ、**Populating Worksheets from a Database** プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## データ ソースの作成  
 **\[データ ソース\]** ウィンドウを使用して、型指定されたデータセットをプロジェクトに追加します。  
  
#### 型指定されたデータセットをプロジェクトに追加するには  
  
1.  **\[データ ソース\]** ウィンドウが表示されていない場合は、メニュー バーの **\[表示\]**、**\[その他のウィンドウ\]**、**\[データ ソース\]** の順にクリックして表示します。  
  
2.  **\[新しいデータ ソースの追加\]** をクリックして**データ ソース構成ウィザード**を開始します。  
  
3.  **\[データベース\]** をクリックして、**\[次へ\]** をクリックします。  
  
4.  `AdventureWorksLT` データベースへの既存の接続がある場合は、その接続を選んで **\[次へ\]** をクリックします。  
  
     それ以外の場合は、**\[新しい接続\]** をクリックし、**\[接続の追加\]** ダイアログ ボックスを使用して新しい接続を作成します。 詳細については、「[方法 : データベース内のデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)」を参照してください。  
  
5.  **\[アプリケーション構成ファイルへの接続文字列を保存\]** ページで、**\[次へ\]** をクリックします。  
  
6.  **\[データベース オブジェクトの選択\]** ページで、**\[テーブル\]** を展開し、**\[Address \(SalesLT\)\]** を選びます。  
  
7.  **\[完了\]** をクリックします。  
  
     AdventureWorksLTDataSet.xsd ファイルが**ソリューション エクスプローラー**に追加されます。 このファイルでは、次の項目を定義します。  
  
    -   `AdventureWorksLTDataSet` という名前の型指定されたデータセット。 このデータセットは、AdventureWorksLT データベースの **Address \(SalesLT\)** テーブルの内容を表します。  
  
    -   TableAdapter という名前の `AddressTableAdapter`。 この TableAdapter は、`AdventureWorksLTDataSet` のデータを読み書きするために使用します。 詳細については、「[TableAdapter の概要](/visual-studio/data-tools/tableadapter-overview)」を参照してください。  
  
     これらのオブジェクトは、どちらもこのチュートリアルの後半で使用します。  
  
## コントロールの作成とデータへのコントロールのバインド  
 このチュートリアルでは、ユーザーがブックを開くとすぐに、事前に選んでおいたテーブル内のすべてのデータが <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールによって表示されます。 リスト オブジェクトは <xref:System.Windows.Forms.BindingSource> を使用してコントロールをデータベースに接続します。  
  
 コントロールのデータへのバインドについて詳しくは、「[Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)」をご覧ください。  
  
#### リスト オブジェクト、データセット、テーブル アダプターを追加するには  
  
1.  `ThisAddIn` クラスで、次のコントロールを宣言し、`AdventureWorksLTDataSet` データセットの `Address` テーブルを表示するようにします。  
  
     [!code-csharp[Trin_ExcelAddInDatabase#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#1)]  
  
2.  `ThisAddIn_Startup` メソッドに次のコードを追加し、データセットを初期化して、そのデータセットに `AdventureWorksLTDataSet` データセットから得た情報を設定します。  
  
     [!code-csharp[Trin_ExcelAddInDatabase#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#2)]  
  
3.  `ThisAddIn_Startup` メソッドに次のコードを追加します。 これによりホスト項目が生成され、ワークシートの機能が拡張されます。 詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
     [!code-csharp[Trin_ExcelAddInDatabase#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#3)]  
  
4.  範囲を作成して <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを追加します。  
  
     [!code-csharp[Trin_ExcelAddInDatabase#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#4)]  
  
5.  <xref:System.Windows.Forms.BindingSource> を使用して、リスト オブジェクトを `AdventureWorksLTDataSet` にバインドします。 リスト オブジェクトにバインドする列の名前を渡します。  
  
     [!code-csharp[Trin_ExcelAddInDatabase#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#5)]  
  
## アドインのテスト  
 Excel を開くと、<xref:Microsoft.Office.Tools.Excel.ListObject> コントロールにより `AdventureWorksLTDataSet` データセットの `Address` テーブルから得られるデータが表示されます。  
  
#### VSTO アドインをテストするには  
  
-   **F5** キーを押します。  
  
     `addressListObject` という名前の <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールがワークシートに作成されます。 同時に、`adventureWorksLTDataSet` という名前のデータセット オブジェクトと、`addressBindingSource` という名前の <xref:System.Windows.Forms.BindingSource> がプロジェクトに追加されます。<xref:Microsoft.Office.Tools.Excel.ListObject> が <xref:System.Windows.Forms.BindingSource> にバインドされ、さらにこれがデータセット オブジェクトにバインドされます。  
  
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
 [Office ソリューションにおけるローカル データベース使用の概要](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Windows フォーム アプリケーションでのデータへの接続](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource コンポーネントの概要](../Topic/BindingSource%20Component%20Overview.md)  
  
  