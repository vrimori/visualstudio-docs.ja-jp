---
title: "Office ソリューションでのコントロールへのデータ バインディング |Microsoft ドキュメント"
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
- Office documents [Office development in Visual Studio], connecting to data
- data, data binding
- data binding
- data binding, Office solutions
- data binding, controls
- Office applications [Office development in Visual Studio], data binding
- controls, data binding
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5892f77b335e26e5b907159c4a9da37a58d2ae19
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="binding-data-to-controls-in-office-solutions"></a>Office ソリューションでのコントロールへのデータのバインド
  Microsoft Office Word 文書または Microsoft Office Excel ワークシート上の Windows フォーム コントロールや *ホスト コントロール* を、データ ソースにバインドできます。この場合、コントロールには自動的にデータが表示されます。 アプリケーション レベルのプロジェクトとドキュメント レベルのプロジェクトの両方で、コントロールにデータをバインドできます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 ホスト コントロールは、Word や Excel のオブジェクト モデルにあるオブジェクトを拡張します。たとえば、Word のコンテンツ コントロールや Excel の名前付き範囲が挙げられます。 詳細については、「 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 Windows フォーム コントロールとホスト コントロールはいずれも Windows フォームのデータ バインディング モデルを使用します。このモデルでは、データセットやデータ テーブルなどのデータ ソースに対して *単純データ バインディング* と *複合データ バインディング* の両方がサポートされます。 Windows フォームにおけるデータ バインディング モデルに関する詳細については、次を参照してください。[データ連結と Windows フォーム](/dotnet/framework/winforms/data-binding-and-windows-forms)です。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[操作方法: 使用するデータベース データ Excel で?](http://go.microsoft.com/fwlink/?LinkID=130287)です。  
  
## <a name="simple-data-binding"></a>単純データ バインディング  
 単純データ バインディングは、コントロール プロパティが、データ テーブル内の値など、単一のデータ要素にバインドされる場合に存在します。 たとえば、 <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールは、データセット内のフィールドにバインドできる <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> プロパティを持ちます。 データセット内のフィールドが変更されると、名前付き範囲内の値も変更されます。 <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールを除くすべてのホスト コントロールが、単純データ バインディングをサポートしています。 <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールはコレクションであるため、データ バインディングをサポートしません。  
  
 ホスト コントロールへの単純データ バインディングを実行するには追加、<xref:System.Windows.Forms.Binding>コントロールのデータ連結プロパティにします。 <xref:System.Windows.Forms.Binding> オブジェクトは、コントロールのプロパティ値とデータ要素の値との間の単純バインディングを表します。  
  
 ドキュメント レベルのプロジェクトにあるデータ要素に <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> プロパティをバインドする方法を、次の例に示します。  
  
 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]  
  
 単純データ バインディングを示すチュートリアルについては、次を参照してください[チュートリアル: ドキュメント レベルのプロジェクトでの単純データ バインディング](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)」ドキュメント レベルのプロジェクトと[チュートリアル: VSTO での単純データ バインディングのアドイン プロジェクト。](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) VSTO アドイン プロジェクト。  
  
## <a name="complex-data-binding"></a>複合データ バインディング  
 複合データ バインディングは、コントロール プロパティが、データ テーブル内の複数の列など、複数のデータ要素にバインドされる場合に存在します。 Excel の <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールは、複合データ バインディングをサポートする唯一のホスト コントロールです。 ただし、複合データ バインディングをサポートする Windows フォーム コントロールが数多くあります ( <xref:System.Windows.Forms.DataGridView> コントロールなど)。  
  
 複合データ バインディングを実行するには、複合データ バインディングでサポートされているデータ ソース オブジェクトにコントロールの DataSource プロパティを設定します。 たとえば、 <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> コントロールの <xref:Microsoft.Office.Tools.Excel.ListObject> プロパティは、データ テーブル内の複数の列にバインドできます。 データ テーブル内のすべてのデータは <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールに表示され、データ テーブル内のデータが変更されると、 <xref:Microsoft.Office.Tools.Excel.ListObject> も変更されます。 複合データ バインディングに使用できるデータ ソースの一覧については、「 [Data Sources Supported by Windows Forms](/dotnet/framework/winforms/data-sources-supported-by-windows-forms)」をご覧ください。  
  
 次のコード例は、2 つの <xref:System.Data.DataSet> オブジェクトを持つ <xref:System.Data.DataTable> を作成し、そのうち 1 つのテーブルにデータを入力します。 次に、コードはデータを含むテーブルに <xref:Microsoft.Office.Tools.Excel.ListObject> をバインドします。 これは、Excel のドキュメント レベルのプロジェクト用の例です。  
  
 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]  
  
 複合データ バインディングを示すチュートリアルについては、次を参照してください[チュートリアル: ドキュメント レベルのプロジェクトでの複合データ バインディング](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)」ドキュメント レベルのプロジェクトと[チュートリアル: VSTO で複合データ バインディングのアドイン プロジェクト。](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) VSTO アドイン プロジェクト。  
  
## <a name="displaying-data-in-documents-and-workbooks"></a>文書およびブック内のデータの表示  
 ドキュメント レベルのプロジェクトでは、Windows フォームで使用する場合と同じように **[データ ソース]** ウィンドウを使用して、文書やブックにデータ バインド コントロールを簡単に追加できます。 使用しての詳細については、**データ ソース**ウィンドウを参照してください[Visual Studio でのデータにコントロールを Windows フォームのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)と[新しいデータ ソースを追加](../data-tools/add-new-data-sources.md)です。  
  
### <a name="dragging-controls-from-the-data-sources-window"></a>[データ ソース] ウィンドウからのコントロールのドラッグ  
 **[データ ソース]** ウィンドウからオブジェクトをドラッグすると、ドキュメントにコントロールが作成されます。 作成されるコントロールの種類は、単一のデータ列をバインドするか、複数のデータ列をバインドするかによって異なります。  
  
 Excel の場合、フィールドごとに <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールがワークシートに作成され、複数の行と列を含むデータ範囲ごとに <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールが作成されます。 この既定の動作を変更するには、 **[データ ソース]** ウィンドウでテーブルまたはフィールドを選び、ドロップダウン リストで別のコントロールを選びます。  
  
 <xref:Microsoft.Office.Tools.Word.ContentControl> コントロールが文書に追加されます。 コンテンツ コントロールの種類は、選んだフィールドのデータ型によって異なります。  
  
### <a name="binding-data-in-document-level-projects-at-design-time"></a>デザイン時におけるドキュメント レベルのプロジェクトでのデータのバインド  
 以下のトピックでは、デザイン時にデータをバインドする例を示しています。  
  
-   [方法: データベースのデータをワークシートに読み込む](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)  
  
-   [方法: データベースからドキュメントにデータを読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)  
  
-   [方法: オブジェクトのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)  
  
-   [方法: サービスのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
-   [方法: ワークシート内でデータベースのレコードをスクロールする](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)  
  
### <a name="binding-data-in-vsto-add-in-projects"></a>VSTO アドイン プロジェクトでのデータのバインド  
 VSTO アドイン プロジェクトでは、コントロールを追加できるのは実行時だけです。 以下のトピックでは、実行時にデータをバインドする例を示しています。  
  
-   [チュートリアル: VSTO アドイン プロジェクトでの単純データ バインディング](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)  
  
-   [チュートリアル: VSTO アドイン プロジェクトでの複合データ バインディング](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)  
  
## <a name="updating-data-that-is-bound-to-host-controls"></a>ホスト コントロールにバインドされているデータの更新  
 データ ソースとホスト コントロールの間のデータ バインディングでは、双方向のデータ更新が必要です。 単純データ バインディングでは、データ ソースでの変更は自動的にホスト コントロールに反映されますが、ホスト コントロールでの変更の場合、明示的な呼び出しによってデータ ソースを更新する必要があります。 これは、別のデータ バインド フィールドで行われた変更が伴わない限り、あるデータ バインド フィールドで行われた変更が受け付けられないことがあるためです。 たとえば、2 つのフィールドがあり、1 つは年齢、1 つは経験年数を示すものとします。 経験年数が年齢を上回ることはありません。 同時に変更しない限り、ユーザーは年齢を 50 から 25 に更新し、経験年数を 30 から 10 に更新することはできません。 この問題を解決するために、単純データ バインディングのフィールドは、更新がコードで明示的に送信されるまで更新されないようになっています。  
  
 単純データ バインディングを有効にしているホスト コントロールからデータ ソースを更新するには、更新をメモリ内データ ソース ( <xref:System.Data.DataSet> や <xref:System.Data.DataTable>など) に送信する必要があります。ソリューションでバックエンド データベースを使用している場合は、バックエンド データベースにも更新を送信する必要があります。  
  
 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを使用して複合データ バインディングを実行するときは、メモリ内データ ソースを明示的に更新する必要はありません。 この場合には、コードを追加しなくても、メモリ内データ ソースに変更が自動的に送信されます。  
  
 詳細については、「 [How to: Update a Data Source with Data from a Host Control](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [操作方法: Excel でデータベースのデータを使用する](http://go.microsoft.com/fwlink/?LinkID=130287)   
 [データ連結と Windows フォーム](/dotnet/framework/winforms/data-binding-and-windows-forms)   
 [方法 : Windows フォームに単純バインド コントロールを作成する](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [データをデータベースに保存します。](../data-tools/save-data-back-to-the-database.md)    
 [TableAdapter を使用してデータを更新します。](../data-tools/update-data-by-using-a-tableadapter.md)    
 [データのキャッシュ](../vsto/caching-data.md)   
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)  
  
  