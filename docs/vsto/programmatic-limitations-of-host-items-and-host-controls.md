---
title: ホスト項目とホスト コントロールのプログラム上の制限事項 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c47b1158eefda91e83ce85a5a7403f3f8f0249a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>ホスト項目およびホスト コントロールのプログラム上の制限事項
  それぞれのホスト項目やホスト コントロールは、それに対応するネイティブな Microsoft Office Word オブジェクトや Microsoft Office Excel オブジェクトと同様に動作するように設計され、さらに追加の機能が備えられています。 ただし、ホスト項目やホスト コントロールと、ネイティブな Office オブジェクトの実行時の動作には、基本的な相違点がいくつかあります。  
  
 ホスト項目とホスト コントロールの概要については、「 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="programmatically-creating-host-items"></a>プログラムによるホスト項目の作成  
 Word または Excel オブジェクト モデルを使用することで、文書、ブック、またはワークシートをプログラムで実行時に作成したり、開いたりする場合、その項目はホスト項目ではありません。 その新しいオブジェクトは、ネイティブな Office オブジェクトです。 たとえば、 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> メソッドを使用して実行時に新しい Word 文書を作成すると、その文書は、 <xref:Microsoft.Office.Interop.Word.Document> ホスト項目ではなく、ネイティブな <xref:Microsoft.Office.Tools.Word.Document> オブジェクトになります。 同様に、 <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> メソッドを使用して実行時に新しいワークシートを作成すると、 <xref:Microsoft.Office.Interop.Excel.Worksheet> ホスト項目ではなく、ネイティブな <xref:Microsoft.Office.Tools.Excel.Worksheet> オブジェクトが作成されます。  
  
 ドキュメント レベルのプロジェクトでは、実行時にホスト項目を作成することはできません。 ドキュメント レベルのプロジェクトでは、デザイン時にのみ、ホスト項目を作成できます 詳細については、「 [Document Host Item](../vsto/document-host-item.md)「 [Workbook Host Item](../vsto/workbook-host-item.md)および「 [Worksheet Host Item](../vsto/worksheet-host-item.md)」を参照してください。  
  
 VSTO アドイン プロジェクトでは、実行時に <xref:Microsoft.Office.Tools.Word.Document>、 <xref:Microsoft.Office.Tools.Excel.Workbook>、または <xref:Microsoft.Office.Tools.Excel.Worksheet> のホスト項目を作成できます。 詳細については、「 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
## <a name="programmatically-creating-host-controls"></a>プログラムによるホスト コントロールの作成  
 実行時に、プログラムによって、 <xref:Microsoft.Office.Tools.Word.Document> ホスト項目または <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目にホスト コントロールを追加できます。 詳細については、「 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
 ネイティブな <xref:Microsoft.Office.Interop.Word.Document> や <xref:Microsoft.Office.Interop.Excel.Worksheet>に、ホスト コントロールを追加することはできません。  
  
> [!NOTE]  
>  ホスト コントロールの <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>、 <xref:Microsoft.Office.Tools.Word.XMLNode>、および <xref:Microsoft.Office.Tools.Word.XMLNodes>は、プログラムによってワークシートや文書に追加することはできません。  
  
## <a name="understanding-type-differences-between-host-items-host-controls-and-native-office-objects"></a>ホスト項目、ホスト コントロールと、ネイティブな Office オブジェクトの相違点について  
 それぞれのホスト項目やホスト コントロールには、基になるネイティブな Microsoft Office Word オブジェクトまたは Microsoft Office Excel オブジェクトがあります。 ホスト項目またはホスト コントロールの InnerObject プロパティを使用して基になるオブジェクトにアクセスすることができます。 ただし、ネイティブな Office オブジェクトをそれに対応するホスト項目またはホスト コントロールにキャストする方法はありません。 ネイティブな Office オブジェクトをホスト項目またはホスト コントロールの型にキャストしようとすると、 <xref:System.InvalidCastException> がスローされます。  
  
 ホスト項目とホスト コントロールの型、および基になるネイティブな Office オブジェクトの違いがコードに影響を及ぼす可能性について、いくつかのシナリオを挙げて説明します。  
  
### <a name="passing-host-controls-to-methods-and-properties"></a>メソッドやプロパティへのホスト コントロールの引き渡し  
 Word では、パラメーターとしてネイティブな Word オブジェクトを要求するメソッドまたはプロパティに、ホスト コントロールを渡すことはできません。 ホスト コントロールの InnerObject プロパティを使用して、基になるネイティブな Word オブジェクトを返す必要があります。 たとえば、メソッドに <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクトを渡す場合は、 <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> ホスト コントロールの <xref:Microsoft.Office.Tools.Word.Bookmark> プロパティを渡します。  
  
 Excel では、メソッドまたはプロパティは、基になる Excel オブジェクトを要求するときに、メソッドまたはプロパティに、ホスト コントロールを渡す、InnerObject、ホスト コントロールのプロパティを使用する必要があります。  
  
 次に示す例では、 <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを作成して、そのコントロールを <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> メソッドに渡しています。 このコードでは、名前付き範囲の <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> プロパティを使用して、 <xref:Microsoft.Office.Interop.Excel.Range> メソッドが要求する、基になる Office の <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> を返します。  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]  
  
### <a name="return-types-of-native-office-methods-and-properties"></a>ネイティブな Office のメソッドとプロパティの戻り値の型  
 ホスト項目のほとんどのメソッドとプロパティは、そのホスト項目の基になっているネイティブな Office オブジェクトを返します。 たとえば、Excel の <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> ホスト コントロールの <xref:Microsoft.Office.Tools.Excel.NamedRange> プロパティは、 <xref:Microsoft.Office.Interop.Excel.Worksheet> ホスト項目ではなく <xref:Microsoft.Office.Tools.Excel.Worksheet> オブジェクトを返します。 同様に、Word の <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> ホスト コントロールの <xref:Microsoft.Office.Tools.Word.RichTextContentControl> プロパティは、 <xref:Microsoft.Office.Interop.Word.Document> ホスト項目ではなく <xref:Microsoft.Office.Tools.Word.Document> オブジェクトを返します。  
  
### <a name="accessing-collections-of-host-controls"></a>ホスト コントロールのコレクションへのアクセス  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] には、ホスト コントロールの種類ごとの個別のコレクションは用意されていません。 代わりに、ホスト項目のコントロール プロパティを使用して、文書またはワークシートに、すべてのマネージ コントロール (ホスト コントロールと Windows フォーム コントロールの両方) を反復処理して、興味のあるホスト コントロールの種類に一致するアイテムを探します。 次に示すコード例では、Word 文書の各コントロールを調べ、そのコントロールが <xref:Microsoft.Office.Tools.Word.Bookmark>かどうかを確認しています。  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]  
  
 ホスト項目のコントロールのプロパティに関する詳細については、次を参照してください。[を実行時に Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)です。  
  
 Word と Excel オブジェクト モデルには、文書とワークシートのネイティブ コントロールのコレクションを公開するプロパティが含まれています。 これらのプロパティを使用してマネージ コントロールにアクセスすることはできません。 たとえば、 <xref:Microsoft.Office.Tools.Word.Bookmark> の <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> プロパティや <xref:Microsoft.Office.Interop.Word.Document> の <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> プロパティを使用して、文書内の各 <xref:Microsoft.Office.Tools.Word.Document>ホスト コントロールを列挙することはできません。 これらのプロパティには、文書内の <xref:Microsoft.Office.Interop.Word.Bookmark> コントロールのみが含まれています。つまり、文書内の <xref:Microsoft.Office.Tools.Word.Bookmark> ホスト コントロールは含まれていないということです。  
  
## <a name="see-also"></a>関連項目  
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Workbook ホスト項目](../vsto/workbook-host-item.md)   
 [Document ホスト項目](../vsto/document-host-item.md)  
  
  