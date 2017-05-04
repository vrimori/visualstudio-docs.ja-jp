---
title: "方法: プログラムによって Word の表を作成する | Microsoft Docs"
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
  - "ドキュメント [Visual Studio での Office 開発], 追加 (テーブルを)"
  - "テーブル [Visual Studio での Office 開発], 追加 (ドキュメントに)"
ms.assetid: fe1f9143-9622-45e8-b0a5-511336d99ad1
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# 方法: プログラムによって Word の表を作成する
  <xref:Microsoft.Office.Interop.Word.Tables> コレクションは <xref:Microsoft.Office.Interop.Word.Document>、<xref:Microsoft.Office.Tools.Word.Document>、<xref:Microsoft.Office.Interop.Word.Selection>、および <xref:Microsoft.Office.Interop.Word.Range> の各クラスのメンバーです。したがって、これらのどのコンテキストでも表を作成できます。  指定した範囲に表を追加するには、<xref:Microsoft.Office.Interop.Word.Tables> コレクションの <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> メソッドを使用します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## ドキュメント レベルのカスタマイズでの表の作成  
  
#### ドキュメントに単純な表を追加するには  
  
-   <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> メソッドを使用して、ドキュメントの先頭に 3 行 4 列の表を追加します。  
  
     次のコード例を使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomation#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#86)]  
  
 表を作成すると、作成した表は自動的に <xref:Microsoft.Office.Tools.Word.Document> ホスト項目の <xref:Microsoft.Office.Interop.Word.Tables> コレクションに追加されます。  表を参照するには、次のコードに示すとおり、<xref:Microsoft.Office.Interop.Word.Tables.Item%2A> プロパティを使用して項目番号で参照します。  
  
#### 項目番号で表を参照するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> プロパティを使用して、参照する表の項目番号を指定します。  
  
     次のコード例を使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomation#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#87)]  
  
 各 <xref:Microsoft.Office.Interop.Word.Table> オブジェクトには <xref:Microsoft.Office.Interop.Word.Table.Range%2A> プロパティもあり、このプロパティを使用して書式設定属性を設定できます。  
  
#### 表にスタイルを適用するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Table.Style%2A> プロパティを使用して、Word のいずれかの組み込みスタイルを表に適用します。  
  
     次のコード例を使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomation#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#88)]  
  
## VSTO アドインでの表の作成  
  
#### ドキュメントに単純な表を追加するには  
  
-   <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> メソッドを使用して、ドキュメントの先頭に 3 行 4 列の表を追加します。  
  
     作業中のドキュメントに表を追加するコード例を次に示します。  このコード例を使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#86)]  
  
 表を作成すると、作成した表は自動的に <xref:Microsoft.Office.Interop.Word.Document> の <xref:Microsoft.Office.Interop.Word.Tables> コレクションに追加されます。  表を参照するには、次のコードに示すとおり、<xref:Microsoft.Office.Interop.Word.Tables.Item%2A> プロパティを使用して項目番号で参照します。  
  
#### 項目番号で表を参照するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> プロパティを使用して、参照する表の項目番号を指定します。  
  
     作業中のドキュメントを使用するコード例を次に示します。  このコード例を使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#87)]  
  
 各 <xref:Microsoft.Office.Interop.Word.Table> オブジェクトには <xref:Microsoft.Office.Interop.Word.Table.Range%2A> プロパティもあり、このプロパティを使用して書式設定属性を設定できます。  
  
#### 表にスタイルを適用するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Table.Style%2A> プロパティを使用して、Word のいずれかの組み込みスタイルを表に適用します。  
  
     作業中のドキュメントを使用するコード例を次に示します。  このコード例を使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#88)]  
  
## 参照  
 [方法: プログラムによって Word の表のセルにテキストと書式設定を追加する](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [方法: プログラムによって Word の表に行と列を追加する](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [方法: プログラムによって Document プロパティを Word の表に読み込む](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  