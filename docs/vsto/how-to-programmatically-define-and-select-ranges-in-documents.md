---
title: "方法: プログラムによって文書に複数の範囲を定義して選択する | Microsoft Docs"
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
  - "ドキュメント [Visual Studio での Office 開発], 範囲"
  - "ドキュメント [Visual Studio での Office 開発], 選択 (文を)"
  - "範囲, 定義 (ドキュメントで)"
  - "範囲, 選択 (ドキュメントで)"
  - "文, 選択 (ドキュメントで)"
ms.assetid: 0727c1cb-d44c-4f1c-a699-4365dd13be5d
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 方法: プログラムによって文書に複数の範囲を定義して選択する
  Microsoft Office Word 文書内に範囲を定義するには、<xref:Microsoft.Office.Interop.Word.Range> オブジェクトを使用します。  文書全体を選択するには、<xref:Microsoft.Office.Interop.Word.Range> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.Select%2A> メソッドを使用する方法や、<xref:Microsoft.Office.Tools.Word.Document> クラス \(ドキュメント レベルのカスタマイズの場合\) または <xref:Microsoft.Office.Interop.Word.Document> クラス \(VSTO アドインの場合\) の Content プロパティを使用する方法など、いくつかの方法があります。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 範囲の定義  
 次の使用例は、作業中の文書の最初の 7 文字 \(非印刷文字を含む\) で構成される新しい <xref:Microsoft.Office.Interop.Word.Range> オブジェクトの作成方法を示します。  次に、範囲内のテキストを選択します。  
  
#### ドキュメント レベルのカスタマイズで範囲を定義するには  
  
1.  文書に範囲を追加するには、<xref:Microsoft.Office.Tools.Word.Document> クラスの <xref:Microsoft.Office.Tools.Word.Document.Range%2A> メソッドに開始文字と終了文字を渡します。  このコード例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomation#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#18)]  
  
#### VSTO アドインを使用して範囲を定義するには  
  
1.  文書に範囲を追加するには、<xref:Microsoft.Office.Interop.Word.Document> クラスの <xref:Microsoft.Office.Interop.Word._Document.Range%2A> メソッドに開始文字と終了文字を渡します。  作業中の文書に範囲を追加するコード例を次に示します。  このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#18)]  
  
## ドキュメント レベルのカスタマイズでの範囲の選択  
 次の例は、<xref:Microsoft.Office.Interop.Word.Range> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.Select%2A> メソッドを使用して、または <xref:Microsoft.Office.Tools.Word.Document> クラスの <xref:Microsoft.Office.Tools.Word.Document.Content%2A> プロパティを使用して文書全体を選択する方法を示しています。  
  
#### Select メソッドを使用して文書全体を範囲として選択するには  
  
1.  文書全体を含む <xref:Microsoft.Office.Interop.Word.Range> の <xref:Microsoft.Office.Interop.Word.Range.Select%2A> メソッドを使用します。  次のコード例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomation#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#19)]  
  
#### Content プロパティを使用して文書全体を範囲として選択するには  
  
1.  <xref:Microsoft.Office.Tools.Word.Document.Content%2A> プロパティを使用して、文書全体を含む範囲を定義します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomation#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#20)]  
  
 また、他のオブジェクトのメソッドとプロパティを使用して範囲を定義することもできます。  
  
#### 作業中の文書の文を選択するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Sentences> コレクション使用して範囲を設定します。  選択する文のインデックスを使用します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomation#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#21)]  
  
 文を選択するもう 1 つの方法として、範囲の開始値と終了値を手動で設定する方法があります。  
  
#### 開始値と終了値を手動で設定して文を選択するには  
  
1.  範囲変数を作成します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomation#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#23)]  
  
2.  文書内に少なくとも 2 つの文があることを確認し、範囲の *Start* 引数と *End* 引数を設定して、範囲を選択します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomation#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#24)]  
  
## VSTO アドインを使用することによる範囲の選択  
 次の例は、<xref:Microsoft.Office.Interop.Word.Range> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.Select%2A> メソッドを使用して、または <xref:Microsoft.Office.Interop.Word.Document> クラスの <xref:Microsoft.Office.Interop.Word._Document.Content%2A> プロパティを使用して文書全体を選択する方法を示しています。  
  
#### Select メソッドを使用して文書全体を範囲として選択するには  
  
1.  文書全体を含む <xref:Microsoft.Office.Interop.Word.Range> の <xref:Microsoft.Office.Interop.Word.Range.Select%2A> メソッドを使用します。  次のコード例では、作業中の文書の内容を選択します。  このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
#### Content プロパティを使用して文書全体を範囲として選択するには  
  
1.  <xref:Microsoft.Office.Interop.Word._Document.Content%2A> プロパティを使用して、文書全体を含む範囲を定義します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
 また、他のオブジェクトのメソッドとプロパティを使用して範囲を定義することもできます。  
  
#### 作業中の文書の文を選択するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Sentences> コレクション使用して範囲を設定します。  選択する文のインデックスを使用します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#21)]  
  
 文を選択するもう 1 つの方法として、範囲の開始値と終了値を手動で設定する方法があります。  
  
#### 開始値と終了値を手動で設定して文を選択するには  
  
1.  範囲変数を作成します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
2.  文書内に少なくとも 2 つの文があることを確認し、範囲の *Start* 引数と *End* 引数を設定して、範囲を選択します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## 参照  
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [方法: プログラムによってドキュメント内の範囲を拡張する](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [方法: 範囲の開始文字と終了文字をプログラムによって取得する](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [方法: プログラムによってドキュメント内の範囲を拡張する](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [方法: プログラムによって Word 文書の範囲をリセットする](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [方法: プログラムによって文書内の範囲または選択範囲を縮小する](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [方法: 範囲を作成するときにプログラムによって段落記号を除外する](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  