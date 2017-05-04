---
title: "方法: プログラムによって文書内の文字数をカウントする | Microsoft Docs"
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
  - "文字、カウント (ドキュメントで)"
  - "カウント (文書の文字数を)"
  - "ドキュメント [Visual Studio での Office 開発]、カウント (文字を)"
ms.assetid: ab64fe87-896a-4b56-bdf8-91c4326b540e
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# 方法: プログラムによって文書内の文字数をカウントする
  ドキュメント内の最初の文字は、挿入ポイントを表す文字位置 0 に位置します。 最後の文字位置は、ドキュメント内の文字数の合計と同じになります。<xref:Microsoft.Office.Interop.Word.Characters> コレクションの <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> のプロパティを使用して、ドキュメント内の文字数を特定することができます。  
  
 スペース、段落記号、通常は表示されないその他の文字を含む、ドキュメント内のすべての文字がカウントされます。 新規作成された空白のドキュメントでも、段落記号が含まれているため、1 文字が返されます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### ドキュメント レベルのカスタマイズで文字数を表示するには  
  
1.  ドキュメント全体を選択します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#98](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#98)]
     [!code-vb[Trin_VstcoreWordAutomation#98](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#98)]  
  
2.  メッセージ ボックスにドキュメント内の文字数が表示されます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#99](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#99)]
     [!code-vb[Trin_VstcoreWordAutomation#99](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#99)]  
  
### VSTO アドインで文字数を表示するには  
  
1.  ドキュメント全体を選択します。 以下の例ではアクティブ ドキュメントが選ばれています。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#98)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#98)]  
  
2.  メッセージ ボックスにドキュメント内の文字数が表示されます。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#99)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#99)]  
  
## 参照  
 [方法: 範囲の開始文字と終了文字をプログラムによって取得する](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [方法: プログラムによって文書に複数の範囲を定義して選択する](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
  
  