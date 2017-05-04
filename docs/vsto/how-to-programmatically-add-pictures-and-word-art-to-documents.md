---
title: "方法: プログラムによって文書に画像およびワードアートを追加する | Microsoft Docs"
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
  - "ドキュメント [Visual Studio での Office 開発], 追加 (ピクチャを)"
  - "グラフィックス, 追加 (Word ドキュメントに)"
  - "Word ドキュメント, 追加 (ピクチャを)"
  - "Word ドキュメント, 追加 (ワードアートを)"
  - "WordArt, 追加 (ドキュメントに)"
ms.assetid: 944e1858-bc7c-471f-b5e7-adf3b0fa574d
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 方法: プログラムによって文書に画像およびワードアートを追加する
  デザイン時または実行時に、画像および描画オブジェクトをドキュメントに追加できます。  ワードアートでは、Microsoft Office Word ドキュメントに装飾的なテキストを追加することができます。  これらの特別なテキスト効果は、ドキュメントに挿入できる、カスタマイズ可能な描画オブジェクトです。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## デザイン時に画像を追加する  
 ドキュメント レベルのカスタマイズを開発している場合は、デザイン時にドキュメントに画像を追加できます。  
  
#### デザイン時に Word 文書に画像を追加するには  
  
1.  ドキュメント内の画像を挿入する場所にカーソルを置きます。  
  
2.  リボンの **\[挿入\]** タブをクリックします。  
  
3.  **\[図\]** グループで、**\[図\]** をクリックします。  
  
4.  **\[図の挿入\]** ダイアログ ボックスで、挿入する画像に移動し、**\[挿入\]** をクリックします。  
  
     画像が、ドキュメントの現在のカーソル位置に追加されます。  
  
## 実行時に画像を追加する  
 現在のカーソル位置でドキュメントに画像を挿入できます。  
  
#### カーソルの場所に画像を追加するには  
  
1.  <xref:Microsoft.Office.Interop.Word.InlineShapes> コレクションの <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> メソッドを呼び出し、ファイル名を渡します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#108](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#108)]
     [!code-vb[Trin_VstcoreWordAutomation#108](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#108)]  
  
## デザイン時にワードアートを追加する  
 ドキュメント レベルのカスタマイズを開発している場合は、デザイン時にドキュメントにワードアートを追加できます。  
  
#### デザイン時にワードアートを Word ドキュメントを追加するには  
  
1.  ドキュメント内のワードアートを挿入する場所にカーソルを置きます。  
  
2.  リボンの **\[挿入\]** タブをクリックします。  
  
3.  **\[テキスト\]** グループで、**\[ワードアート\]** をクリックし、ワードアートのスタイルをクリックします。  
  
4.  ドキュメント内に表示するテキストを、**\[ワードアート テキストの編集\]** ダイアログ ボックスに追加し、**\[OK\]** をクリックします。  
  
     選択したワードアート スタイルが適用されたテキストが、ドキュメントに追加されます。  
  
## 実行時にワードアートを追加する  
 現在のカーソル位置でドキュメントにワードアートを挿入できます。  ドキュメント レベルのカスタマイズと VSTO アドインでは、手順が異なります。  
  
#### ドキュメント レベルのカスタマイズで、カーソル位置にワードアートを追加するには  
  
1.  現在のカーソル位置の左と上の位置を取得します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomation#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#109)]  
  
2.  ドキュメント内の <xref:Microsoft.Office.Interop.Word.Shapes> オブジェクトの <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomation#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#110)]  
  
#### VSTO アドインでカーソル位置にワードアートを追加するには  
  
1.  現在のカーソル位置の左と上の位置を取得します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#109)]  
  
2.  作業中のドキュメント \(または指定した別のドキュメント\) の <xref:Microsoft.Office.Interop.Word.Shapes> オブジェクトの <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#110)]  
  
## コードのコンパイル  
  
-   ドライブ C 上に **SamplePicture.jpg** という名前の画像が存在する必要があります。  
  
## 参照  
 [方法: プログラムによって既存文書を開く](../vsto/how-to-programmatically-open-existing-documents.md)   
 [方法: プログラムによって Word 文書にテキストを挿入する](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [方法: プログラムによって検索後に選択範囲を復元する](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [方法: プログラムによって文書を保存する](../vsto/how-to-programmatically-save-documents.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  