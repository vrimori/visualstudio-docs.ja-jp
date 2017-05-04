---
title: "方法: 範囲の開始文字と終了文字をプログラムによって取得する | Microsoft Docs"
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
  - "範囲、取得 (開始文字と終了文字を)"
  - "終了文字"
  - "開始文字"
  - "ドキュメント [Visual Studio での Office 開発]、取得 (範囲を)"
ms.assetid: 734c630c-abc9-491d-94b6-429d1fc7a4cc
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# 方法: 範囲の開始文字と終了文字をプログラムによって取得する
  この例では、範囲の開始位置と終了位置の文字位置を取得する方法を示します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### ドキュメント レベルのカスタマイズ内の範囲の先頭と末尾の文字を取得するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Range> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.Start%2A> プロパティおよび <xref:Microsoft.Office.Interop.Word.Range.End%2A> プロパティの値を取得します。 次のコード例では、ドキュメントの 2 番目の文の開始位置と終了位置を取得します。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#25)]  
  
### VSTO アドインを使用して、範囲の先頭と末尾の文字を取得するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Range> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.Start%2A> プロパティおよび <xref:Microsoft.Office.Interop.Word.Range.End%2A> プロパティの値を取得します。 次のコード例では、アクティブなドキュメントの 2 番目の文の開始位置と終了位置を取得します。 このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
## 参照  
 [方法: プログラムによって文書に複数の範囲を定義して選択する](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [方法: プログラムによってドキュメント内の範囲を拡張する](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [方法: プログラムによって Word 文書の範囲をリセットする](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [方法: プログラムによって文書内の範囲または選択範囲を縮小する](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [方法: 範囲を作成するときにプログラムによって段落記号を除外する](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [方法: プログラムによって文書内の文字数をカウントする](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  