---
title: "方法: プログラムによって文書内のテキストに書式を設定する"
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
  - "書式設定 [Visual Studio での Office 開発]"
  - "ドキュメント [Visual Studio での Office 開発]、書式設定 (テキスト)"
  - "テキスト [Visual Studio での Office 開発]、書式設定 (文書の)"
ms.assetid: 0a84893b-5ccc-4515-a2dc-95773ee8eaba
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 方法: プログラムによって文書内のテキストに書式を設定する
  <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを使用することにより、Microsoft Office Word 文書のテキストの書式を設定できます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 次の例では、文書内の最初の段落を選択し、フォント サイズ、フォント名、およびアラインメントを変更します。 次に、範囲を選択し、コードの次のセクションを実行する前に一時停止するためのメッセージ ボックスを表示します。 次のセクションでは、<xref:Microsoft.Office.Tools.Word.Document> ホスト項目 \(ドキュメント レベルのカスタマイズの場合\) または <xref:Microsoft.Office.Interop.Word.Document> クラス \(VSTO アドインの場合\) の Undo メソッドを 3 回呼び出します。 標準のインデント スタイルを適用し、メッセージ ボックスを表示してコードを一時停止します。 最後に、<xref:Microsoft.Office.Tools.Word.Document.Undo%2A> メソッドを 1 回呼び出し、メッセージ ボックスを表示します。  
  
## ドキュメント レベルのカスタマイズの例  
  
#### ドキュメント レベルのカスタマイズを使用してテキストの書式を設定するには  
  
1.  次のコード例はドキュメント レベルのカスタマイズで使用できます。 このコードを使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#62)]  
  
## VSTO アドインの例  
  
#### VSTO アドインを使用してテキストを書式設定するには  
  
1.  次の例は VSTO アドインで使用できます。 この例ではアクティブ ドキュメントを使用します。 このコードを使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#62)]  
  
## 参照  
 [方法: プログラムによって文書に複数の範囲を定義して選択する](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [方法: プログラムによって Word 文書にテキストを挿入する](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [方法: プログラムによって文書内のテキストを検索および置換する](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  