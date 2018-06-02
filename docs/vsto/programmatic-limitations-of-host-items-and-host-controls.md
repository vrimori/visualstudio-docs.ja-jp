---
title: ホスト項目とホスト コントロールのプログラム上の制限事項
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
ms.openlocfilehash: 0b7e45ed9ba8e9fcd42d57a1cc6aaf34ce3e3711
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693384"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>ホスト項目とホスト コントロールのプログラム上の制限事項
  それぞれのホスト項目やホスト コントロールは、それに対応するネイティブな Microsoft Office Word オブジェクトや Microsoft Office Excel オブジェクトと同様に動作するように設計され、さらに追加の機能が備えられています。 ただし、ホスト項目やホスト コントロールと、ネイティブな Office オブジェクトの実行時の動作には、基本的な相違点がいくつかあります。  
  
 ホスト項目とホスト コントロールの概要については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)です。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="programmatically-create-host-items"></a>ホスト項目をプログラムによって作成します。  
 Word または Excel オブジェクト モデルを使用することで、文書、ブック、またはワークシートをプログラムで実行時に作成したり、開いたりする場合、その項目はホスト項目ではありません。 その新しいオブジェクトは、ネイティブな Office オブジェクトです。 たとえば、 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> メソッドを使用して実行時に新しい Word 文書を作成すると、その文書は、 <xref:Microsoft.Office.Interop.Word.Document> ホスト項目ではなく、ネイティブな <xref:Microsoft.Office.Tools.Word.Document> オブジェクトになります。 同様に、 <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> メソッドを使用して実行時に新しいワークシートを作成すると、 <xref:Microsoft.Office.Interop.Excel.Worksheet> ホスト項目ではなく、ネイティブな <xref:Microsoft.Office.Tools.Excel.Worksheet> オブジェクトが作成されます。  
  
 ドキュメント レベルのプロジェクトでは、実行時にホスト項目を作成できません。 ドキュメント レベルのプロジェクトでは、デザイン時にのみ、ホスト項目を作成できます 詳細については、次を参照してください。 [Document ホスト項目](../vsto/document-host-item.md)、 [Workbook ホスト項目](../vsto/workbook-host-item.md)、および[Worksheet ホスト項目](../vsto/worksheet-host-item.md)です。  
  
 VSTO アドイン プロジェクトで作成できます<xref:Microsoft.Office.Tools.Word.Document>、 <xref:Microsoft.Office.Tools.Excel.Workbook>、または<xref:Microsoft.Office.Tools.Excel.Worksheet>実行時に項目をホストします。 詳細については、次を参照してください。[拡張 Word 文書と実行時に VSTO アドイン内の Excel ブック](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)です。  
  
## <a name="programmatically-create-host-controls"></a>ホスト コントロールをプログラムによって作成します。  
 ホスト コントロールをプログラムで追加することができます、<xref:Microsoft.Office.Tools.Word.Document>または<xref:Microsoft.Office.Tools.Excel.Worksheet>実行時にホスト項目。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)です。  
  
 ネイティブな <xref:Microsoft.Office.Interop.Word.Document> や <xref:Microsoft.Office.Interop.Excel.Worksheet>に、ホスト コントロールを追加することはできません。  
  
> [!NOTE]  
>  ホスト コントロールの <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>、 <xref:Microsoft.Office.Tools.Word.XMLNode>、および <xref:Microsoft.Office.Tools.Word.XMLNodes>は、プログラムによってワークシートや文書に追加することはできません。  
  
## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>ホスト項目、ホスト コントロールとネイティブな Office オブジェクト間の型の違いを理解します。  
 それぞれのホスト項目やホスト コントロールには、基になるネイティブな Microsoft Office Word オブジェクトまたは Microsoft Office Excel オブジェクトがあります。 ホスト項目またはホスト コントロールの InnerObject プロパティを使用して基になるオブジェクトにアクセスすることができます。 ただし、ネイティブな Office オブジェクトをそれに対応するホスト項目またはホスト コントロールにキャストする方法はありません。 ネイティブな Office オブジェクトをホスト項目またはホスト コントロールの型にキャストしようとすると、 <xref:System.InvalidCastException> がスローされます。  
  
 ホスト項目とホスト コントロールの型、および基になるネイティブな Office オブジェクトの違いがコードに影響を及ぼす可能性について、いくつかのシナリオを挙げて説明します。  
  
### <a name="pass-host-controls-to-methods-and-properties"></a>メソッドとプロパティにホスト コントロールを渡す  
 Word では、パラメーターとしてネイティブな Word オブジェクトを要求するメソッドまたはプロパティに、ホスト コントロールを渡すことはできません。 ホスト コントロールの InnerObject プロパティを使用して、基になるネイティブな Word オブジェクトを返す必要があります。 たとえば、メソッドに <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクトを渡す場合は、 <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> ホスト コントロールの <xref:Microsoft.Office.Tools.Word.Bookmark> プロパティを渡します。  
  
 Excel では、メソッドまたはプロパティは、基になる Excel オブジェクトを要求するときに、メソッドまたはプロパティに、ホスト コントロールを渡す、InnerObject、ホスト コントロールのプロパティを使用する必要があります。  
  
 次に示す例では、 <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを作成して、そのコントロールを <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> メソッドに渡しています。 このコードでは、名前付き範囲の <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> プロパティを使用して、 <xref:Microsoft.Office.Interop.Excel.Range> メソッドが要求する、基になる Office の <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> を返します。  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]  
  
### <a name="return-types-of-native-office-methods-and-properties"></a>ネイティブな Office のメソッドとプロパティの型を返す  
 ホスト項目のほとんどのメソッドとプロパティは、そのホスト項目の基になっているネイティブな Office オブジェクトを返します。 たとえば、Excel の <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> ホスト コントロールの <xref:Microsoft.Office.Tools.Excel.NamedRange> プロパティは、 <xref:Microsoft.Office.Interop.Excel.Worksheet> ホスト項目ではなく <xref:Microsoft.Office.Tools.Excel.Worksheet> オブジェクトを返します。 同様に、Word の <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> ホスト コントロールの <xref:Microsoft.Office.Tools.Word.RichTextContentControl> プロパティは、 <xref:Microsoft.Office.Interop.Word.Document> ホスト項目ではなく <xref:Microsoft.Office.Tools.Word.Document> オブジェクトを返します。  
  
### <a name="access-collections-of-host-controls"></a>ホスト コントロールのコレクションのアクセス  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] には、ホスト コントロールの種類ごとの個別のコレクションは用意されていません。 代わりに、ホスト項目のコントロール プロパティを使用して、文書またはワークシートに、すべてのマネージ コントロール (ホスト コントロールと Windows フォーム コントロールの両方) を反復処理して、興味のあるホスト コントロールの種類に一致するアイテムを探します。 次に示すコード例では、Word 文書の各コントロールを調べ、そのコントロールが <xref:Microsoft.Office.Tools.Word.Bookmark>かどうかを確認しています。  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]  
  
 ホスト項目のコントロールのプロパティに関する詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)です。  
  
 Word と Excel オブジェクト モデルには、文書とワークシートのネイティブ コントロールのコレクションを公開するプロパティが含まれています。 これらのプロパティを使用してマネージ コントロールにアクセスすることはできません。 たとえば、 <xref:Microsoft.Office.Tools.Word.Bookmark> の <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> プロパティや <xref:Microsoft.Office.Interop.Word.Document> の <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> プロパティを使用して、文書内の各 <xref:Microsoft.Office.Tools.Word.Document>ホスト コントロールを列挙することはできません。 これらのプロパティには、文書内の <xref:Microsoft.Office.Interop.Word.Bookmark> コントロールのみが含まれています。つまり、文書内の <xref:Microsoft.Office.Tools.Word.Bookmark> ホスト コントロールは含まれていないということです。  
  
## <a name="see-also"></a>関連項目  
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)   
 [拡張オブジェクトによる Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Workbook ホスト項目](../vsto/workbook-host-item.md)   
 [Document ホスト項目](../vsto/document-host-item.md)  
  
  