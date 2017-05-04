---
title: "方法: プログラムによってブックマークのテキストを更新する | Microsoft Docs"
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
  - "Bookmark コントロール, 更新 (内容を)"
  - "ブックマーク, 更新 (テキストを)"
  - "テキスト [Visual Studio での Office 開発], 更新 (ブックマークを)"
ms.assetid: 2324164d-2538-4695-9aaf-7285ce403be3
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 方法: プログラムによってブックマークのテキストを更新する
  Microsoft Office Word 文書のプレースホルダー ブックマークにテキストを挿入することにより、そのテキストを後で取得したり、ブックマーク内のテキストを置き換えたりすることができます。  ドキュメント レベルのカスタマイズを開発している場合は、データにバインドされた <xref:Microsoft.Office.Tools.Word.Bookmark> コントロール内のテキストを更新することもできます。  詳細については、「[Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)」を参照してください。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ブックマーク オブジェクトには次の 2 種類があります。  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark> ホスト コントロール。  
  
     <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールは、ネイティブ <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクトを拡張したもので、データのバインドが可能になり、イベントが公開されます。  ホスト コントロールの詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
-   ネイティブ <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクト。  
  
     <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクトには、イベントや、データのバインド機能はありません。  
  
 ブックマークにテキストを割り当てる場合、<xref:Microsoft.Office.Interop.Word.Bookmark> と <xref:Microsoft.Office.Tools.Word.Bookmark> の動作は異なります。  詳細については、「[Bookmark コントロール](../vsto/bookmark-control.md)」を参照してください。  
  
## ホスト コントロールの使用  
  
#### Bookmark コントロールを使用してブックマークの内容を更新するには  
  
1.  ブックマークの名前を指定する引数 `bookmark` と <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> プロパティに割り当てる文字列を指定する引数 `newText` を受け取るプロシージャを作成します。  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールの <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> または <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> プロパティにテキストを割り当てても、ブックマークは削除されません。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#63)]
     [!code-vb[Trin_VstcoreWordAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#63)]  
  
2.  文字列 *newText* を <xref:Microsoft.Office.Tools.Word.Bookmark> の <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> プロパティに割り当てます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#64)]
     [!code-vb[Trin_VstcoreWordAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#64)]  
  
## Word のオブジェクトの使用  
  
#### Word の Bookmark オブジェクトを使用してブックマークの内容を更新するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Bookmark> の名前を指定する引数 `bookmark` とブックマークの <xref:Microsoft.Office.Interop.Word.Range.Text%2A> プロパティに割り当てる文字列を指定する引数 `newText` を受け取るプロシージャを作成します。  
  
    > [!NOTE]  
    >  Word のネイティブ <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクトにテキストを割り当てると、ブックマークは削除されます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#65](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#65)]
     [!code-vb[Trin_VstcoreWordAutomation#65](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#65)]  
  
2.  文字列 *newText* をブックマークの <xref:Microsoft.Office.Interop.Word.Range.Text%2A> プロパティに割り当てます。これによって、ブックマークが自動的に削除されます。  その後、<xref:Microsoft.Office.Interop.Word.Bookmarks> コレクションにブックマークを再び追加します。  
  
     次のコード例はドキュメント レベルのカスタマイズで使用できます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomation#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#66)]  
  
     次のコード例は VSTO アドインで使用できます。  この例ではアクティブ ドキュメントを使用します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#66)]  
  
## 参照  
 [方法: プログラムによって Word 文書にテキストを挿入する](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [Bookmark コントロール](../vsto/bookmark-control.md)  
  
  