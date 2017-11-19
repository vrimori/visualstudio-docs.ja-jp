---
title: "方法: ホスト コントロールからのデータでデータ ソースを更新 |Microsoft ドキュメント"
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
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
ms.assetid: b91025af-1eaa-44ee-88f2-71ecaa7a0440
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1fd4716e81d280e049a8cbd1a5206b52f2714e27
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>方法 : ホスト コントロールからのデータでデータ ソースを更新する
  ホスト コントロールをデータ ソースにバインドし、コントロール内のデータに加えられた変更でデータ ソースを更新することができます。 この処理には主に 2 つの手順があります。  
  
1.  コントロールで変更されたデータを使用して、メモリ内データ ソースを更新します。 一般に、メモリ内データ ソースは <xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、またはその他のデータ オブジェクトです。  
  
2.  メモリ内データ ソースで変更されたデータを使用して、データベースを更新します。 これは、データ ソースが SQL Server や Microsoft Office Access データベースなどのバックエンド データベースに接続されている場合にのみ有効です。  
  
 ホスト コントロールとデータ バインディングの詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)と[Office ソリューションでのコントロールへのデータ バインディング](../vsto/binding-data-to-controls-in-office-solutions.md)です。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="updating-the-in-memory-data-source"></a>メモリ内データ ソースの更新  
 既定では、単純データ バインディングを有効にしているホスト コントロール (Word 文書のコンテンツ コントロールや Excel ワークシートの名前付き範囲コントロールなど) は、データの変更内容をメモリ内データ ソースに保存しません。 つまり、エンド ユーザーがホスト コントロールの値に変更を加えてからコントロールの外に移動すると、コントロールの新しい値は自動的にはデータ ソースに保存されません。  
  
 データ ソースにデータを保存するには、実行時に特定のイベントに応答してデータ ソースを更新するコードを記述します。または、コントロールの値が変更されたときに自動的にデータ ソースを更新するようにコントロールを構成することもできます。  
  
 メモリ内データ ソースに <xref:Microsoft.Office.Tools.Excel.ListObject> の変更を保存する必要はありません。 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールをデータにバインドすると、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールは追加のコードなしで変更内容を自動的にメモリ内データ ソースに保存します。  
  
#### <a name="to-update-the-in-memory-data-source-at-run-time"></a>実行時にメモリ内データ ソースを更新するには  
  
-   コントロールをデータ ソースにバインドする <xref:System.Windows.Forms.Binding.WriteValue%2A> オブジェクトの <xref:System.Windows.Forms.Binding> メソッドを呼び出します。  
  
     Excel ワークシートの <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールに加えられた変更をデータ ソースに保存する例を次に示します。 この例は、 <xref:Microsoft.Office.Tools.Excel.NamedRange> という名前の `namedRange1` コントロールで <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> プロパティがデータ ソースのフィールドにバインドされていることを前提としています。  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]  
  
### <a name="automatically-updating-the-in-memory-data-source"></a>メモリ内データ ソースの自動更新  
 メモリ内データ ソースを自動的に更新するように、コントロールを構成することもできます。 ドキュメント レベルのプロジェクトでこれを行うには、コードまたはデザイナーを使用します。 VSTO アドイン プロジェクトでは、コードを使用する必要があります。  
  
##### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>コードを使用してメモリ内データ ソースを自動的に更新するようにコントロールを設定するには  
  
1.  System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged モードを使用して、<xref:System.Windows.Forms.Binding>データ ソースにコントロールをバインドするオブジェクト。 データ ソースの更新には 2 つのオプションがあります。  
  
    -   コントロールが検証されると、データ ソースを更新するには、System.Windows.Forms.DataSourceUpdateMode.OnValidation にこのプロパティを設定します。  
  
    -   コントロールのデータ バインドされたプロパティの値が変更されたときに、データ ソースを更新するには、System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged にこのプロパティを設定します。  
  
        > [!NOTE]  
        >  Word ではないプラン文書変更やコントロール変更の通知はため System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged オプションは、Word ホスト コントロールに適用されません。 ただし、Word 文書上の Windows フォーム コントロールには、このオプションを使用できます。  
  
     コントロールの値が変わると自動的にデータ ソースを更新するように <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを構成する例を次に示します。 この例は、 <xref:Microsoft.Office.Tools.Excel.NamedRange> という名前の `namedRange1` コントロールで <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> プロパティがデータ ソースのフィールドにバインドされていることを前提としています。  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]  
  
##### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>デザイナーを使用してメモリ内データ ソースを自動的に更新するようにコントロールを設定するには  
  
1.  Visual Studio のデザイナーで、Word 文書または Excel ブックを開きます。  
  
2.  データ ソースの自動更新を行うコントロールをクリックします。  
  
3.  **[プロパティ]** ウィンドウで **(DataBindings)** プロパティを展開します。  
  
4.  横に、 **(詳細)**プロパティ、省略記号ボタン (![VisualStudioEllipsesButton スクリーン ショット](../vsto/media/vbellipsesbutton.png "VisualStudioEllipsesButton スクリーン ショット"))。  
  
5.  **[フォーマットと詳細バインド]** ダイアログ ボックスで、 **[データ ソース更新モード]** ドロップダウン リストをクリックし、次の値のいずれかを選びます。  
  
    -   コントロールの検証時にデータ ソースを更新するには、 **[OnValidation]**を選びます。  
  
    -   コントロールのデータ バインド プロパティの値が変更されたときにデータ ソースを更新するには、 **[OnPropertyChanged]**を選びます。  
  
        > [!NOTE]  
        >  **[OnPropertyChanged]** オプションは、Word ホスト コントロールには適用されません。Word では文書変更やコントロール変更の通知は提供されないためです。 ただし、Word 文書上の Windows フォーム コントロールには、このオプションを使用できます。  
  
6.  **[フォーマットと詳細バインド]** ダイアログ ボックスを閉じます。  
  
## <a name="updating-the-database"></a>データベースの更新  
 メモリ内データ ソースがデータベースに関連付けられている場合、データ ソースへの変更内容を使用して、データベースを更新する必要があります。 データベースの更新の詳細については、次を参照してください。[データをデータベースに保存](../data-tools/save-data-back-to-the-database.md)と[TableAdapter を使用してデータ更新](../data-tools/update-data-by-using-a-tableadapter.md)です。  
  
#### <a name="to-update-the-database"></a>データベースを更新するには  
  
1.  コントロールの <xref:System.Windows.Forms.BindingSource.EndEdit%2A> の <xref:System.Windows.Forms.BindingSource> メソッドを呼び出します。  
  
     デザイン時に文書またはブックにデータ バインド コントロールを追加すると、 <xref:System.Windows.Forms.BindingSource> が自動的に生成されます。 <xref:System.Windows.Forms.BindingSource> によって、コントロールはプロジェクト内の型指定されたデータセットに接続されます。 詳細については、「 [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview)」を参照してください。  
  
     次のコード例は、プロジェクトに <xref:System.Windows.Forms.BindingSource> という名前の `customersBindingSource`が含まれていることを前提としています。  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]  
  
2.  呼び出す、`Update`プロジェクトで生成された TableAdapter のメソッドです。  
  
     TableAdapter はデザイン時に文書またはブックにデータ バインド コントロールを追加するときに自動的に生成されます。 TableAdapter では、データベースに、プロジェクト内の型指定されたデータセットを接続します。 詳細については、「 [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)」を参照してください。  
  
     次のコード例では、Northwind データベースの Customers テーブルへの接続があることと、という名前の TableAdapter を含むプロジェクト`customersTableAdapter`という名前の型指定されたデータセットと`northwindDataSet`です。  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [データをデータベースに保存します。](../data-tools/save-data-back-to-the-database.md)    
 [TableAdapter を使用してデータを更新します。](../data-tools/update-data-by-using-a-tableadapter.md)    
 [方法: ワークシート内のデータベース レコードをスクロールします。](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [方法: データベースからデータをワークシートに読み込む](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [方法: オブジェクトからのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [方法: データベースからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [方法: サービスのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  