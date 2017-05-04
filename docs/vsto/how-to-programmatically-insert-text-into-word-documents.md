---
title: "方法: プログラムによって Word 文書にテキストを挿入する | Microsoft Docs"
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
  - "範囲、文書へのテキスト挿入"
  - "テキスト [Visual Studio での Office 開発]、文書への挿入"
  - "範囲、文書のテキスト置換"
  - "文書 [Visual Studio での Office 開発]、テキストの挿入"
  - "テキスト [Visual Studio での Office 開発]、置換"
ms.assetid: 405d7442-8ba3-4fcc-b17e-7b289ffd3967
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# 方法: プログラムによって Word 文書にテキストを挿入する
  Microsoft Office Word の文書にテキストを挿入するには、主に次の 3 つの方法があります。  
  
-   範囲内にテキストを挿入する。  
  
-   範囲内のテキストを新しいテキストに置換する。  
  
-   <xref:Microsoft.Office.Interop.Word.Selection> オブジェクトの <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> メソッドを使用して、カーソルの位置または選択範囲にテキストを挿入する。  
  
> [!NOTE]  
>  テキストをコンテンツ コントロールやブックマークに挿入することもできます。 詳細については、次のトピックを参照してください。[コンテンツ コントロール](../vsto/content-controls.md) および[Bookmark コントロール](../vsto/bookmark-control.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 範囲内へのテキストの挿入  
 <xref:Microsoft.Office.Interop.Word.Range> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.Text%2A> プロパティを使用して、文書にテキストを挿入します。  
  
#### 範囲内にテキストを挿入するには  
  
1.  文書の先頭に範囲を指定し、**New Text** というテキストを挿入します。  
  
     次のコード例はドキュメント レベルのカスタマイズで使用できます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#51)]
     [!code-vb[Trin_VstcoreWordAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#51)]  
  
     次のコード例は VSTO アドインで使用できます。 このコードでは作業中のドキュメントを使用します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#51)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#51)]  
  
2.  1 文字から挿入したテキストの長さまで拡張された <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを選択します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#52)]
     [!code-vb[Trin_VstcoreWordAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#52)]  
  
## 範囲内のテキストの置換  
 指定した範囲にテキストが含まれている場合は、範囲内のすべてのテキストが挿入したテキストで置換されます。  
  
#### 範囲内のテキストを置換するには  
  
1.  文書の先頭の 12 文字から成る <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを作成します。  
  
     次のコード例はドキュメント レベルのカスタマイズで使用できます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#53)]
     [!code-vb[Trin_VstcoreWordAutomation#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#53)]  
  
     次のコード例は VSTO アドインで使用できます。 このコードでは作業中のドキュメントを使用します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#53)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#53)]  
  
2.  これらの文字を **New Text** という文字列で置換します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#54](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#54)]
     [!code-vb[Trin_VstcoreWordAutomation#54](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#54)]  
  
3.  範囲を選択します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#55](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#55)]
     [!code-vb[Trin_VstcoreWordAutomation#55](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#55)]  
  
## TypeText を使用したテキストの挿入  
 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> メソッドは、選択範囲にテキストを挿入します。<xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> の動作は、ユーザーのコンピューターで設定されているオプションによって異なります。 次のプロシージャのコードは、<xref:Microsoft.Office.Interop.Word.Selection> オブジェクト変数を宣言し、**Overtype** オプションがオンになっている場合はオフにします。**Overtype** オプションが有効になっていると、カーソル位置の隣にあるテキストが上書きされます。  
  
#### TypeText メソッドを使用してテキストを挿入するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Selection> オブジェクト変数を宣言します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#57)]
     [!code-vb[Trin_VstcoreWordAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#57)]  
  
2.  **Overtype** オプションがオンの場合はオフにします。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#58)]
     [!code-vb[Trin_VstcoreWordAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#58)]  
  
3.  現在の選択範囲が挿入ポイントであるかどうかを確認します。  
  
     選択範囲が挿入位置である場合は、<xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> を使用して文を挿入し、<xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> メソッドを使用して段落記号を挿入します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#59)]
     [!code-vb[Trin_VstcoreWordAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#59)]  
  
4.  **ElseIf** ブロック内のコードで、選択範囲が通常の選択範囲であるかどうかを確認します。 通常の選択範囲である場合は、次の **If** ブロックで、**ReplaceSelection** オプションがオンになっているかどうかを確認します。 オンである場合は、選択範囲の <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> メソッドを使用して、選択範囲を選択されているテキスト ブロックの先頭の挿入ポイントに折りたたみます。 テキストと段落記号を挿入します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#60)]
     [!code-vb[Trin_VstcoreWordAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#60)]  
  
5.  選択範囲が挿入ポイントでも選択テキストのブロックではない場合、**Else** ブロックのコードは何も実行しません。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#61)]
     [!code-vb[Trin_VstcoreWordAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#61)]  
  
 <xref:Microsoft.Office.Interop.Word.Selection> オブジェクトの <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> メソッドを使用することもできます。このメソッドは、キーボードの BackSpace キーと同じ動作をします。 ただし、テキストの挿入および操作については、<xref:Microsoft.Office.Interop.Word.Range> オブジェクトの方がより細かく制御できます。  
  
 完全なコード例を次に示します。 この例を使用するには、プロジェクトの `ThisDocument` クラスか `ThisAddIn` クラスからコードを実行します。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#56](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#56)]
 [!code-vb[Trin_VstcoreWordAutomation#56](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#56)]  
  
## 参照  
 [方法: プログラムによって文書内のテキストに書式を設定する](../vsto/how-to-programmatically-format-text-in-documents.md)   
 [方法: プログラムによって文書に複数の範囲を定義して選択する](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [方法: プログラムによってドキュメント内の範囲を拡張する](../vsto/how-to-programmatically-extend-ranges-in-documents.md)  
  
  