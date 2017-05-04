---
title: "方法: 範囲を作成するときにプログラムによって段落記号を除外する | Microsoft Docs"
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
  - "ドキュメント [Visual Studio でのOffice 開発]、除外 (段落)"
  - "範囲、除外 (Word で段落記号を)"
  - "ドキュメント [Visual Studio での Office 開発]、段落記号"
  - "段落、制御 (構造体の)"
ms.assetid: 6d563834-34bd-4462-a556-4339d9277eee
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# 方法: 範囲を作成するときにプログラムによって段落記号を除外する
  段落に基づいて <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを作成する場合、段落記号などの印刷されない文字はすべて範囲に含まれています。 出力先の段落に、元の段落からテキストを挿入したい場合があります。 出力先の段落を複数の段落に分割したくない場合、元の段落から段落記号を最初に削除する必要があります。 また、段落の書式設定情報は段落記号に格納されるので、範囲を既存の段落に挿入するとき、この情報を含めないようにすることもできます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 次の手順の例では、2 つの文字列変数を宣言し、アクティブなドキュメント内の最初と 2 番目の段落の内容を取得し、その内容を入れ替えます。 その後、<xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> メソッドを使用して範囲から段落記号を削除し、段落内にテキストを挿入しています。  
  
### テキストを挿入するときに、段落の構造を制御するには  
  
1.  最初と 2 番目の段落の 2 つの範囲変数を作成して、<xref:Microsoft.Office.Interop.Word.Range.Text%2A> プロパティを使用してその内容を取得します。  
  
     次のコード例はドキュメント レベルのカスタマイズで使用できます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#27)]  
  
     次のコード例はアプリケーション レベルの VSTO アドインで使用できます。 このコードでは作業中のドキュメントを使用します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
2.  2 つの段落の間のテキストを入れ替え、<xref:Microsoft.Office.Interop.Word.Range.Text%2A> プロパティを割り当てます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#28)]
     [!code-vb[Trin_VstcoreWordAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#28)]  
  
3.  範囲を順に選択し、一時停止してメッセージ ボックスに結果を表示します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#29)]
     [!code-vb[Trin_VstcoreWordAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#29)]  
  
4.  <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> メソッドを使用して `firstRange` を調整し、段落記号が `firstRange` に含まれないようにします。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreWordAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#30)]  
  
5.  最初の段落の残りのテキストを置換して、新しい文字列を範囲の <xref:Microsoft.Office.Interop.Word.Range.Text%2A> プロパティに割り当てます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreWordAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#31)]  
  
6.  `secondRange` のテキストを置換して、段落記号を含めます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#32)]
     [!code-vb[Trin_VstcoreWordAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#32)]  
  
7.  `firstRange` を選択し、一時停止してメッセージ ボックスに結果を表示して、`secondRange` と同じ操作を行います。  
  
     `firstRange` が再定義され、段落記号が除外されると段落の元の書式が保持されます。 ただし、文が `secondRange` の段落記号の上に挿入されると、別の段落が削除されます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#33)]
     [!code-vb[Trin_VstcoreWordAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#33)]  
  
     2 つの範囲の元の内容は文字列として保存されているため、ドキュメントを元の状態に復元することができます。  
  
8.  1 文字分の位置に <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> メソッドを使用して `firstRange` を再調整 し、段落記号を含めます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#34](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreWordAutomation#34](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#34)]  
  
9. `secondRange` を削除します。 これにより、3 段落目が元の位置に戻ります。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#35](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#35)]
     [!code-vb[Trin_VstcoreWordAutomation#35](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#35)]  
  
10. `firstRange` に元の段落テキストを復元します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#36](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#36)]
     [!code-vb[Trin_VstcoreWordAutomation#36](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#36)]  
  
11. <xref:Microsoft.Office.Interop.Word.Range> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> メソッドを使用して元の 2 段落目の内容を `firstRange` の後に挿入し、`firstRange` を選択します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#37](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#37)]
     [!code-vb[Trin_VstcoreWordAutomation#37](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#37)]  
  
## ドキュメント レベルのカスタマイズの例  
  
#### ドキュメント レベルのカスタマイズでテキストを挿入するときに段落の構造を制御するには  
  
1.  次の例は、ドキュメント レベルのカスタマイズのメソッド全体を示しています。 このコードを使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#26)]  
  
## VSTO アドインの例  
  
#### VSTO アドインにテキストを挿入するときに、段落の構造を制御するには  
  
1.  次の例は、VSTO アドインのメソッド全体を示しています。 このコードを使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
## 参照  
 [方法: プログラムによってドキュメント内の範囲を拡張する](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [方法: プログラムによって文書内の範囲または選択範囲を縮小する](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [方法: プログラムによって Word 文書にテキストを挿入する](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [方法: プログラムによって Word 文書の範囲をリセットする](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [方法: プログラムによって文書に複数の範囲を定義して選択する](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  