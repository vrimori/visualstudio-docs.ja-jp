---
title: "方法: プログラムによって文書内のテキストにコメントを追加する | Microsoft Docs"
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
  - "コメント、ドキュメントへの追加"
  - "ドキュメント [Visual Studio での Office 開発]、追加 (コメントの)"
ms.assetid: 4e396e31-01bf-424c-be6b-9a1806bcd572
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 方法: プログラムによって文書内のテキストにコメントを追加する
  Document クラスの Comments プロパティは、Microsoft Office の Word 文書内のテキストの範囲にコメントを追加します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 次の例は、文書の最初の段落にコメントを追加します。  
  
### ドキュメント レベルのカスタマイズで、新しいコメントをテキストに追加するには  
  
1.  <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> プロパティの <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> メソッドを呼び出し、範囲とコメントのテキストを入力します。 次のコード例を使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#118](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#118)]
     [!code-vb[Trin_VstcoreWordAutomation#118](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#118)]  
  
### VSTO アドインのテキストに新しいコメントを追加するには  
  
1.  <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> プロパティの <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> メソッドを呼び出し、範囲とコメントのテキストを入力します。  
  
     作業中の文書にコメントを追加するコード例を次に示します。 このコード例を使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#118)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#118)]  
  
## 信頼性の高いプログラミング  
 Word によってコメントに追加されるユーザーの頭文字を変更するには、<xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> プロパティを使用します。  
  
## 参照  
 [方法: プログラムによって文書からすべてのコメントを削除する](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Document ホスト項目](../vsto/document-host-item.md)  
  
  