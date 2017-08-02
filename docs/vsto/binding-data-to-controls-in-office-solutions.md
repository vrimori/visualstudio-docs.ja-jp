---
title: "Office ソリューションでのコントロールへのデータのバインド"
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
  - "Office ドキュメント [Visual Studio での Office 開発]、接続 (データに)"
  - "データ、データ バインディング"
  - "データ バインディング"
  - "データ バインディング、Office ソリューション"
  - "データ バインディング、コントロール"
  - "Office アプリケーション [Visual Studio での Office 開発]、データ バインディング"
  - "コントロール、データ バインディング"
ms.assetid: b6faaed7-df9b-4d78-9863-e515cd5c7ed9
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Office ソリューションでのコントロールへのデータのバインド
  Microsoft Office Word 文書または Microsoft Office Excel ワークシート上の Windows フォーム コントロールや*ホスト コントロール*を、データ ソースにバインドできます。この場合、コントロールには自動的にデータが表示されます。 アプリケーション レベルのプロジェクトとドキュメント レベルのプロジェクトの両方で、コントロールにデータをバインドできます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 ホスト コントロールは、Word や Excel のオブジェクト モデルにあるオブジェクトを拡張します。たとえば、Word のコンテンツ コントロールや Excel の名前付き範囲が挙げられます。 詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 Windows フォーム コントロールとホスト コントロールはいずれも Windows フォームのデータ バインディング モデルを使用します。このモデルでは、データセットやデータ テーブルなどのデータ ソースに対して*単純データ バインディング*と*複合データ バインディング*の両方がサポートされます。 Windows フォームでのデータ バインディング モデルについて詳しくは、「[データ連結と Windows フォーム](../Topic/Data%20Binding%20and%20Windows%20Forms.md)」をご覧ください。  
  
 ![ビデオへのリンク](~/docs/data-tools/media/playvideo.gif "ビデオへのリンク") 関連のビデオ デモについては、「[操作方法: Excel でデータベースのデータを使用する](http://go.microsoft.com/fwlink/?LinkID=130287)」をご覧ください。  
  
## 単純データ バインディング  
 単純データ バインディングは、コントロール プロパティが、データ テーブル内の値など、単一のデータ要素にバインドされる場合に存在します。 たとえば、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールは、データセット内のフィールドにバインドできる <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> プロパティを持ちます。 データセット内のフィールドが変更されると、名前付き範囲内の値も変更されます。<xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールを除くすべてのホスト コントロールが、単純データ バインディングをサポートしています。<xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールはコレクションであるため、データ バインディングをサポートしません。  
  
 ホスト コントロールへの単純データ バインディングを実行するには、コントロールの DataBindings プロパティに <xref:System.Windows.Forms.Binding> を追加します。<xref:System.Windows.Forms.Binding> オブジェクトは、コントロールのプロパティ値とデータ要素の値との間の単純バインディングを表します。  
  
 ドキュメント レベルのプロジェクトにあるデータ要素に <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> プロパティをバインドする方法を、次の例に示します。  
  
 [!code-csharp[Trin_BindableComponent#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_BindableComponent/CS/Sheet1.cs#4)]
 [!code-vb[Trin_BindableComponent#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_BindableComponent/VB/Sheet1.vb#4)]  
  
 単純データ バインディングを示すチュートリアルについては、「[チュートリアル : ドキュメント レベルのプロジェクトでの単純データ バインド](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)」\(ドキュメント レベルのプロジェクトの場合\) および「[チュートリアル: VSTO アドイン プロジェクトでの単純データ バインディング](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)」\(VSTO アドイン プロジェクトの場合\) をご覧ください。  
  
## 複合データ バインディング  
 複合データ バインディングは、コントロール プロパティが、データ テーブル内の複数の列など、複数のデータ要素にバインドされる場合に存在します。 Excel の <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールは、複合データ バインディングをサポートする唯一のホスト コントロールです。 ただし、複合データ バインディングをサポートする Windows フォーム コントロールが数多くあります \(<xref:System.Windows.Forms.DataGridView> コントロールなど\)。  
  
 複合データ バインディングを実行するには、コントロールの DataSource プロパティを、複合データ バインディングでサポートされるデータ ソース オブジェクトに設定します。 たとえば、<xref:Microsoft.Office.Tools.Excel.ListObject> コントロールの <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> プロパティは、データ テーブル内の複数の列にバインドできます。 データ テーブル内のすべてのデータは <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールに表示され、データ テーブル内のデータが変更されると、<xref:Microsoft.Office.Tools.Excel.ListObject> も変更されます。 複合データ バインディングに使用できるデータ ソースの一覧については、「[Windows フォームがサポートするデータ ソース](../Topic/Data%20Sources%20Supported%20by%20Windows%20Forms.md)」をご覧ください。  
  
 次のコード例は、2 つの <xref:System.Data.DataTable> オブジェクトを持つ <xref:System.Data.DataSet> を作成し、そのうち 1 つのテーブルにデータを入力します。 次に、コードはデータを含むテーブルに <xref:Microsoft.Office.Tools.Excel.ListObject> をバインドします。 これは、Excel のドキュメント レベルのプロジェクト用の例です。  
  
 [!code-csharp[Trin_ExcelListObject#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelListObject/CS/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelListObject/VB/Sheet1.vb#18)]  
  
 複合データ バインディングを示すチュートリアルについては、「[チュートリアル : ドキュメント レベルのプロジェクトでの複合データ バインド](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)」\(ドキュメント レベルのプロジェクトの場合\) および「[チュートリアル : VSTO アドイン プロジェクトでの複合データ バインディング](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)」\(VSTO アドイン プロジェクトの場合\) をご覧ください。  
  
## 文書およびブック内のデータの表示  
 ドキュメント レベルのプロジェクトでは、Windows フォームで使用する場合と同じように **\[データ ソース\]** ウィンドウを使用して、文書やブックにデータ バインド コントロールを簡単に追加できます。**\[データ ソース\]** ウィンドウの使用方法について詳しくは、「[Visual Studio でのデータへの Windows フォーム コントロールのバインド](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)」および「[ウィンドウ](../Topic/Data%20Sources%20Window.md)」をご覧ください。  
  
### \[データ ソース\] ウィンドウからのコントロールのドラッグ  
 **\[データ ソース\]** ウィンドウからオブジェクトをドラッグすると、ドキュメントにコントロールが作成されます。 作成されるコントロールの種類は、単一のデータ列をバインドするか、複数のデータ列をバインドするかによって異なります。  
  
 Excel の場合、フィールドごとに <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールがワークシートに作成され、複数の行と列を含むデータ範囲ごとに <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールが作成されます。 この既定の動作を変更するには、**\[データ ソース\]** ウィンドウでテーブルまたはフィールドを選び、ドロップダウン リストで別のコントロールを選びます。  
  
 <xref:Microsoft.Office.Tools.Word.ContentControl> コントロールが文書に追加されます。 コンテンツ コントロールの種類は、選んだフィールドのデータ型によって異なります。  
  
### デザイン時におけるドキュメント レベルのプロジェクトでのデータのバインド  
 以下のトピックでは、デザイン時にデータをバインドする例を示しています。  
  
-   [方法 : データベースのデータをワークシートに読み込む](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)  
  
-   [方法 : データベースからドキュメントにデータを読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)  
  
-   [方法 : オブジェクトのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)  
  
-   [方法 : サービスのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
-   [方法 : ワークシート内でデータベースのレコードをスクロールする](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)  
  
### VSTO アドイン プロジェクトでのデータのバインド  
 VSTO アドイン プロジェクトでは、コントロールを追加できるのは実行時だけです。 以下のトピックでは、実行時にデータをバインドする例を示しています。  
  
-   [チュートリアル: VSTO アドイン プロジェクトでの単純データ バインディング](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)  
  
-   [チュートリアル : VSTO アドイン プロジェクトでの複合データ バインディング](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)  
  
## ホスト コントロールにバインドされているデータの更新  
 データ ソースとホスト コントロールの間のデータ バインディングでは、双方向のデータ更新が必要です。 単純データ バインディングでは、データ ソースでの変更は自動的にホスト コントロールに反映されますが、ホスト コントロールでの変更の場合、明示的な呼び出しによってデータ ソースを更新する必要があります。 これは、別のデータ バインド フィールドで行われた変更が伴わない限り、あるデータ バインド フィールドで行われた変更が受け付けられないことがあるためです。 たとえば、2 つのフィールドがあり、1 つは年齢、1 つは経験年数を示すものとします。 経験年数が年齢を上回ることはありません。 同時に変更しない限り、ユーザーは年齢を 50 から 25 に更新し、経験年数を 30 から 10 に更新することはできません。 この問題を解決するために、単純データ バインディングのフィールドは、更新がコードで明示的に送信されるまで更新されないようになっています。  
  
 単純データ バインディングを有効にしているホスト コントロールからデータ ソースを更新するには、更新をメモリ内データ ソース \(<xref:System.Data.DataSet> や <xref:System.Data.DataTable> など\) に送信する必要があります。ソリューションでバックエンド データベースを使用している場合は、バックエンド データベースにも更新を送信する必要があります。  
  
 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを使用して複合データ バインディングを実行するときは、メモリ内データ ソースを明示的に更新する必要はありません。 この場合には、コードを追加しなくても、メモリ内データ ソースに変更が自動的に送信されます。  
  
 詳細については、「[方法 : ホスト コントロールからのデータでデータ ソースを更新する](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)」を参照してください。  
  
## 参照  
 [操作方法: Excel でデータベースのデータを使用する](http://go.microsoft.com/fwlink/?LinkID=130287)   
 [データ連結と Windows フォーム](../Topic/Data%20Binding%20and%20Windows%20Forms.md)   
 [方法 : Windows フォームに単純バインド コントロールを作成する](../Topic/How%20to:%20Create%20a%20Simple-Bound%20Control%20on%20a%20Windows%20Form.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [データセットのデータの保存](../Topic/Saving%20data%20back%20to%20the%20database.md)   
 [方法 : TableAdapter を使用してデータを更新する](../data-tools/update-data-by-using-a-tableadapter.md)   
 [キャッシュされたデータ](../vsto/caching-data.md)   
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)  
  
  