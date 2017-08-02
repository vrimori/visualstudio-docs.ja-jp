---
title: "方法 : ホスト コントロールからのデータでデータ ソースを更新する"
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
  - "ドキュメント [Visual Studio での Office 開発]、データ ソースの更新"
  - "データ [Visual Studio での Office 開発]、更新 (データ ソースをドキュメントから)"
  - "ホスト コントロール [Visual Studio での Office 開発]、データ ソースの更新"
  - "Office ドキュメント [Visual Studio での Office 開発、データ ソース"
ms.assetid: b91025af-1eaa-44ee-88f2-71ecaa7a0440
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# 方法 : ホスト コントロールからのデータでデータ ソースを更新する
  ホスト コントロールをデータ ソースにバインドし、コントロール内のデータに加えられた変更でデータ ソースを更新することができます。 この処理には主に 2 つの手順があります。  
  
1.  コントロールで変更されたデータを使用して、メモリ内データ ソースを更新します。 一般に、メモリ内データ ソースは <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、またはその他のデータ オブジェクトです。  
  
2.  メモリ内データ ソースで変更されたデータを使用して、データベースを更新します。 これは、データ ソースが SQL Server や Microsoft Office Access データベースなどのバックエンド データベースに接続されている場合にのみ有効です。  
  
 ホスト コントロールとデータ バインディングについて詳しくは、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」および「[Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)」をご覧ください。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## メモリ内データ ソースの更新  
 既定では、単純データ バインディングを有効にしているホスト コントロール \(Word 文書のコンテンツ コントロールや Excel ワークシートの名前付き範囲コントロールなど\) は、データの変更内容をメモリ内データ ソースに保存しません。 つまり、エンド ユーザーがホスト コントロールの値に変更を加えてからコントロールの外に移動すると、コントロールの新しい値は自動的にはデータ ソースに保存されません。  
  
 データ ソースにデータを保存するには、実行時に特定のイベントに応答してデータ ソースを更新するコードを記述します。または、コントロールの値が変更されたときに自動的にデータ ソースを更新するようにコントロールを構成することもできます。  
  
 メモリ内データ ソースに <xref:Microsoft.Office.Tools.Excel.ListObject> の変更を保存する必要はありません。<xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをデータにバインドすると、<xref:Microsoft.Office.Tools.Excel.ListObject> コントロールは追加のコードなしで変更内容を自動的にメモリ内データ ソースに保存します。  
  
#### 実行時にメモリ内データ ソースを更新するには  
  
-   コントロールをデータ ソースにバインドする <xref:System.Windows.Forms.Binding> オブジェクトの <xref:System.Windows.Forms.Binding.WriteValue%2A> メソッドを呼び出します。  
  
     Excel ワークシートの <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールに加えられた変更をデータ ソースに保存する例を次に示します。 この例は、`namedRange1` という名前の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールで <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> プロパティがデータ ソースのフィールドにバインドされていることを前提としています。  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#1)]  
  
### メモリ内データ ソースの自動更新  
 メモリ内データ ソースを自動的に更新するように、コントロールを構成することもできます。 ドキュメント レベルのプロジェクトでこれを行うには、コードまたはデザイナーを使用します。 VSTO アドイン プロジェクトでは、コードを使用する必要があります。  
  
##### コードを使用してメモリ内データ ソースを自動的に更新するようにコントロールを設定するには  
  
1.  コントロールをデータ ソースにバインドする <xref:System.Windows.Forms.Binding> オブジェクトの System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged  モードを使用します。 データ ソースの更新には 2 つのオプションがあります。  
  
    -   コントロールの検証時にデータ ソースを更新するには、このプロパティを System.Windows.Forms.DataSourceUpdateMode.OnValidation に設定します。  
  
    -   コントロールのデータ バインド プロパティの値が変更されたときにデータ ソースを更新するには、このプロパティを System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged に設定します。  
  
        > [!NOTE]  
        >  System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged オプションは、Word ホスト コントロールには適用されません。Word では文書変更やコントロール変更の通知は提供されないためです。 ただし、Word 文書上の Windows フォーム コントロールには、このオプションを使用できます。  
  
     コントロールの値が変わると自動的にデータ ソースを更新するように <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを構成する例を次に示します。 この例は、`namedRange1` という名前の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールで <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> プロパティがデータ ソースのフィールドにバインドされていることを前提としています。  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#19)]  
  
##### デザイナーを使用してメモリ内データ ソースを自動的に更新するようにコントロールを設定するには  
  
1.  Visual Studio のデザイナーで、Word 文書または Excel ブックを開きます。  
  
2.  データ ソースの自動更新を行うコントロールをクリックします。  
  
3.  **\[プロパティ\]** ウィンドウで **\(DataBindings\)** プロパティを展開します。  
  
4.  **\(Advanced\)** プロパティの横にある省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](~/docs/vsto/media/vbellipsesbutton.png "VisualStudioEllipsesButton スクリーンショット")\) をクリックします。  
  
5.  **\[フォーマットと詳細バインド\]** ダイアログ ボックスで、**\[データ ソース更新モード\]** ドロップダウン リストをクリックし、次の値のいずれかを選びます。  
  
    -   コントロールの検証時にデータ ソースを更新するには、**\[OnValidation\]** を選びます。  
  
    -   コントロールのデータ バインド プロパティの値が変更されたときにデータ ソースを更新するには、**\[OnPropertyChanged\]** を選びます。  
  
        > [!NOTE]  
        >  **\[OnPropertyChanged\]** オプションは、Word ホスト コントロールには適用されません。Word では文書変更やコントロール変更の通知は提供されないためです。 ただし、Word 文書上の Windows フォーム コントロールには、このオプションを使用できます。  
  
6.  **\[フォーマットと詳細バインド\]** ダイアログ ボックスを閉じます。  
  
## データベースの更新  
 メモリ内データ ソースがデータベースに関連付けられている場合、データ ソースへの変更内容を使用して、データベースを更新する必要があります。 データベース更新について詳しくは、「[データセットのデータの保存](../Topic/Saving%20data%20back%20to%20the%20database.md)」および「[方法 : TableAdapter を使用してデータを更新する](../data-tools/update-data-by-using-a-tableadapter.md)」をご覧ください。  
  
#### データベースを更新するには  
  
1.  コントロールの <xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.EndEdit%2A> メソッドを呼び出します。  
  
     デザイン時に文書またはブックにデータ バインド コントロールを追加すると、<xref:System.Windows.Forms.BindingSource> が自動的に生成されます。<xref:System.Windows.Forms.BindingSource> によって、コントロールはプロジェクト内の型指定されたデータセットに接続されます。 詳細については、「[BindingSource コンポーネントの概要](../Topic/BindingSource%20Component%20Overview.md)」を参照してください。  
  
     次のコード例は、プロジェクトに `customersBindingSource` という名前の <xref:System.Windows.Forms.BindingSource> が含まれていることを前提としています。  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#20)]  
  
2.  プロジェクトで生成された TableAdapter の `Update` メソッドを呼び出します。  
  
     デザイン時に文書またはブックにデータ バインド コントロールを追加すると、TableAdapter が自動的に生成されます。TableAdapter によって、プロジェクト内の型指定されたデータセットはデータベースに接続されます。 詳細については、「[TableAdapter の概要](/visual-studio/data-tools/tableadapter-overview)」を参照してください。  
  
     次のコード例は、Northwind データベースの Customers テーブルに接続し、プロジェクトには `customersTableAdapter` という名前の TableAdapter と `northwindDataSet` という名前の型指定されたデータセットが含まれていることを前提としています。  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#21)]  
  
## 参照  
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [データセットのデータの保存](../Topic/Saving%20data%20back%20to%20the%20database.md)   
 [方法 : TableAdapter を使用してデータを更新する](../data-tools/update-data-by-using-a-tableadapter.md)   
 [方法 : ワークシート内でデータベースのレコードをスクロールする](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [方法 : データベースのデータをワークシートに読み込む](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [方法 : オブジェクトのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [方法 : データベースからドキュメントにデータを読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [方法 : サービスのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  