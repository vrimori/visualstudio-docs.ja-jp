---
title: "方法: プログラムによって文書からすべてのコメントを削除する"
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
  - "ドキュメント [Visual Studio での Office 開発]、削除 (コメントを)"
  - "コメント、削除 (ドキュメントから)"
ms.assetid: 920de39a-3b6d-4682-bca6-f4b4dedda1ac
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 方法: プログラムによって文書からすべてのコメントを削除する
  DeleteAllComments メソッドを使用して、Microsoft Office Word 文書からすべてのコメントを削除します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### ドキュメント レベルのカスタマイズの一部であるドキュメントから、すべてのコメントを削除するには  
  
1.  プロジェクトの `ThisDocument` クラスの <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> メソッドを呼び出します。 このコード例を使用するには、`ThisDocument` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomation#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#119)]  
  
### VSTO アドインを使用して、ドキュメントからすべてのコメントを削除するには  
  
1.  コメントを削除する <xref:Microsoft.Office.Interop.Word.Document> から <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> メソッドを呼び出します。  
  
     次に示すコード例では、アクティブ ドキュメントからすべてのコメントを削除します。 このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#119)]  
  
## 参照  
 [方法: プログラムによって文書内のテキストにコメントを追加する](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Document ホスト項目](../vsto/document-host-item.md)  
  
  