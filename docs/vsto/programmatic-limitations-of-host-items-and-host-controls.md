---
title: "ホスト項目およびホスト コントロールのプログラム上の制限事項"
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
  - "Office ドキュメント [Visual Studio での Office 開発、ホスト コントロール"
  - "アプリケーション開発 [Visual Studio での Office 開発]、ホスト項目"
  - "Office アプリケーション [Visual Studio での Office 開発]、ホスト項目"
  - "ホスト項目 [Visual Studio での Office 開発]、プログラム上の制限事項"
  - "Excel [Visual Studio での Office 開発]、ホスト項目"
  - "ホスト コントロール [Visual Studio での Office 開発]、作成"
  - "ドキュメント レベルのカスタマイズ [Visual Studio での Office 開発]、ホスト コントロール"
  - "Office アプリケーション [Visual Studio での Office 開発]、ホスト コントロール"
  - "ドキュメント [Visual Studio での Office 開発]、ホスト コントロール"
  - "コントロール [Visual Studio での Office 開発]、ホスト コントロール"
  - "ホスト コントロール [Visual Studio での Office 開発]、渡す (メソッドおよびプロパティへ)"
  - "アプリケーション開発 [Visual Studio での Office 開発]、ホスト コントロール"
  - "Excel [Visual Studio での Office 開発]、ホスト コントロール"
  - "ホスト コントロール [Visual Studio での Office 開発]、プログラム上の制限事項"
  - "ドキュメント [Visual Studio での Office 開発]、ホスト項目"
  - "Office ドキュメント [Visual Studio での Office 開発]、ホスト項目"
  - "Word [Visual Studio での Office 開発]、ホスト項目"
  - "ドキュメント レベルのカスタマイズ [Visual Studio での Office 開発]、ホスト項目"
  - "Word [Visual Studio での Office 開発]、ホスト コントロール"
ms.assetid: 88487946-6f3d-4ea6-8de0-dd219b8002df
caps.latest.revision: 67
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# ホスト項目およびホスト コントロールのプログラム上の制限事項
  それぞれのホスト項目やホスト コントロールは、それに対応するネイティブな Microsoft Office Word オブジェクトや Microsoft Office Excel オブジェクトと同様に動作するように設計され、さらに追加の機能が備えられています。 ただし、ホスト項目やホスト コントロールと、ネイティブな Office オブジェクトの実行時の動作には、基本的な相違点がいくつかあります。  
  
 ホスト項目とホスト コントロールの概要については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## プログラムによるホスト項目の作成  
 Word または Excel オブジェクト モデルを使用することで、文書、ブック、またはワークシートをプログラムで実行時に作成したり、開いたりする場合、その項目はホスト項目ではありません。 その新しいオブジェクトは、ネイティブな Office オブジェクトです。 たとえば、<xref:Microsoft.Office.Interop.Word.Documents.Add%2A> メソッドを使用して実行時に新しい Word 文書を作成すると、その文書は、<xref:Microsoft.Office.Tools.Word.Document> ホスト項目ではなく、ネイティブな <xref:Microsoft.Office.Interop.Word.Document> オブジェクトになります。 同様に、<xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> メソッドを使用して実行時に新しいワークシートを作成すると、<xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目ではなく、ネイティブな <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトが作成されます。  
  
 ドキュメント レベルのプロジェクトでは、実行時にホスト項目を作成することはできません。 ドキュメント レベルのプロジェクトでは、デザイン時にのみ、ホスト項目を作成できます 詳細については、「[Document ホスト項目](../vsto/document-host-item.md)「[Workbook ホスト項目](../vsto/workbook-host-item.md)および「[Worksheet ホスト項目](../vsto/worksheet-host-item.md)」を参照してください。  
  
 VSTO アドイン プロジェクトでは、実行時に <xref:Microsoft.Office.Tools.Word.Document>、<xref:Microsoft.Office.Tools.Excel.Workbook>、または <xref:Microsoft.Office.Tools.Excel.Worksheet> のホスト項目を作成できます。 詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
## プログラムによるホスト コントロールの作成  
 実行時に、プログラムによって、<xref:Microsoft.Office.Tools.Word.Document> ホスト項目または <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目にホスト コントロールを追加できます。 詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
 ネイティブな <xref:Microsoft.Office.Interop.Word.Document> や <xref:Microsoft.Office.Interop.Excel.Worksheet> に、ホスト コントロールを追加することはできません。  
  
> [!NOTE]  
>  ホスト コントロールの <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>、<xref:Microsoft.Office.Tools.Word.XMLNode>、および <xref:Microsoft.Office.Tools.Word.XMLNodes> は、プログラムによってワークシートや文書に追加することはできません。  
  
## ホスト項目、ホスト コントロールと、ネイティブな Office オブジェクトの相違点について  
 それぞれのホスト項目やホスト コントロールには、基になるネイティブな Microsoft Office Word オブジェクトまたは Microsoft Office Excel オブジェクトがあります。 基になるオブジェクトには、ホスト項目またはホスト コントロールの InnerObject プロパティを使用してアクセスできます。 ただし、ネイティブな Office オブジェクトをそれに対応するホスト項目またはホスト コントロールにキャストする方法はありません。 ネイティブな Office オブジェクトをホスト項目またはホスト コントロールの型にキャストしようとすると、<xref:System.InvalidCastException> がスローされます。  
  
 ホスト項目とホスト コントロールの型、および基になるネイティブな Office オブジェクトの違いがコードに影響を及ぼす可能性について、いくつかのシナリオを挙げて説明します。  
  
### メソッドやプロパティへのホスト コントロールの引き渡し  
 Word では、パラメーターとしてネイティブな Word オブジェクトを要求するメソッドまたはプロパティに、ホスト コントロールを渡すことはできません。 基になるネイティブな Word オブジェクトを返すには、ホスト コントロールの InnerObject プロパティを使用する必要があります。 たとえば、メソッドに <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクトを渡す場合は、<xref:Microsoft.Office.Tools.Word.Bookmark> ホスト コントロールの <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> プロパティを渡します。  
  
 Excel では、メソッドまたはプロパティが基になる Excel オブジェクトを要求するときに、そのメソッドまたはプロパティにホスト コントロールを渡す場合は、ホスト コントロールの InnerObject のプロパティを使用する必要があります。  
  
 次に示す例では、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを作成して、そのコントロールを <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> メソッドに渡しています。 このコードでは、名前付き範囲の <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> プロパティを使用して、<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> メソッドが要求する、基になる Office の <xref:Microsoft.Office.Interop.Excel.Range> を返します。  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#28)]  
  
### ネイティブな Office のメソッドとプロパティの戻り値の型  
 ホスト項目のほとんどのメソッドとプロパティは、そのホスト項目の基になっているネイティブな Office オブジェクトを返します。 たとえば、Excel の <xref:Microsoft.Office.Tools.Excel.NamedRange> ホスト コントロールの <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> プロパティは、<xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目ではなく <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトを返します。 同様に、Word の <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ホスト コントロールの <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> プロパティは、<xref:Microsoft.Office.Tools.Word.Document> ホスト項目ではなく <xref:Microsoft.Office.Interop.Word.Document> オブジェクトを返します。  
  
### ホスト コントロールのコレクションへのアクセス  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] には、ホスト コントロールの種類ごとの個別のコレクションは用意されていません。 その代わりに、ホスト項目の Controls プロパティを使用して、文書またはワークシート内のすべてのマネージ コントロール \(ホスト コントロールと Windows フォーム コントロールの両方\) を反復処理し、目的とする型のホスト コントロールと一致する項目を検索できます。 次に示すコード例では、Word 文書の各コントロールを調べ、そのコントロールが <xref:Microsoft.Office.Tools.Word.Bookmark> かどうかを確認しています。  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#10)]  
  
 ホスト項目の Controls プロパティの詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
 Word と Excel オブジェクト モデルには、文書とワークシートのネイティブ コントロールのコレクションを公開するプロパティが含まれています。 これらのプロパティを使用してマネージ コントロールにアクセスすることはできません。 たとえば、<xref:Microsoft.Office.Interop.Word.Document> の <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> プロパティや <xref:Microsoft.Office.Tools.Word.Document> の <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> プロパティを使用して、文書内の各 <xref:Microsoft.Office.Tools.Word.Bookmark> ホスト コントロールを列挙することはできません。 これらのプロパティには、文書内の <xref:Microsoft.Office.Interop.Word.Bookmark> コントロールのみが含まれています。つまり、文書内の <xref:Microsoft.Office.Tools.Word.Bookmark> ホスト コントロールは含まれていないということです。  
  
## 参照  
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Workbook ホスト項目](../vsto/workbook-host-item.md)   
 [Document ホスト項目](../vsto/document-host-item.md)  
  
  