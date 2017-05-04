---
title: "方法: プログラムによって Word 文書の範囲をリセットする | Microsoft Docs"
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
  - "ドキュメント [Visual Studio での Office 開発]、リセット (範囲を)"
  - "範囲、リセット (ドキュメントで)"
ms.assetid: 45ea9434-e548-4d24-938f-4f1ffa5010d0
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# 方法: プログラムによって Word 文書の範囲をリセットする
  <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> メソッドを使用して、Microsoft Office の Word 文書で既存の範囲のサイズを変更します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 既存の範囲をリセットするには  
  
1.  ドキュメント内の最初の 7 つの文字で始まる最初の範囲を設定します。  
  
     次のコード例はドキュメント レベルのカスタマイズで使用できます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#43](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#43)]
     [!code-vb[Trin_VstcoreWordAutomation#43](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#43)]  
  
     次のコード例は VSTO アドインで使用できます。 このコードでは作業中のドキュメントを使用します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#43)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#43)]  
  
2.  <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> を使用して、2 番目の文から範囲を開始し、5 番目の文の末尾までで範囲を終了します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#44](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#44)]
     [!code-vb[Trin_VstcoreWordAutomation#44](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#44)]  
  
## ドキュメント レベルのカスタマイズの例  
  
#### ドキュメント レベルのカスタマイズで既存の範囲をリセットするには  
  
1.  次の例は、ドキュメント レベルのカスタマイズの例全体を示しています。 このコードを使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#42](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#42)]
     [!code-vb[Trin_VstcoreWordAutomation#42](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#42)]  
  
## VSTO アドインの例  
  
#### VSTO アドインで既存の範囲をリセットするには  
  
1.  次の例は、VSTO アドインの例全体を示しています。 このコードを使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#42)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#42)]  
  
## 参照  
 [方法: プログラムによってドキュメント内の範囲を拡張する](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [方法: プログラムによって文書に複数の範囲を定義して選択する](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [方法: 範囲の開始文字と終了文字をプログラムによって取得する](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [方法: プログラムによって文書内の範囲または選択範囲を縮小する](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)  
  
  