---
title: "方法: プログラムによって文書内のテキストを検索および置換する | Microsoft Docs"
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
  - "ドキュメント [Visual Studio での Office 開発], 検索"
  - "テキスト [Visual Studio での Office 開発], 検索 (文書を)"
  - "テキスト [Visual Studio での Office 開発], テキスト検索"
  - "テキスト検索, ドキュメント"
  - "テキスト検索, 置換 (テキストを)"
ms.assetid: a66962f5-eeb9-4dc6-a70f-9039ab437a63
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# 方法: プログラムによって文書内のテキストを検索および置換する
  <xref:Microsoft.Office.Interop.Word.Find> オブジェクトは <xref:Microsoft.Office.Interop.Word.Selection> および <xref:Microsoft.Office.Interop.Word.Range> オブジェクトの両方のメンバーであり、どちらを使用しても Microsoft Office Word ドキュメント内のテキストを検索できます。  Replace コマンドは、Find コマンドの拡張機能です。  
  
 <xref:Microsoft.Office.Interop.Word.Find> オブジェクトを使用して Microsoft Office Word ドキュメントをループ処理し、特定のテキスト、書式、またはスタイルを検索し、<xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> プロパティを使用して検出された項目を置き換えます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Selection オブジェクトの使用  
 テキストを検索するために <xref:Microsoft.Office.Interop.Word.Selection> オブジェクトを使用する場合、指定する検索条件は現在選択されているテキストにしか適用されません。  <xref:Microsoft.Office.Interop.Word.Selection> が挿入ポイントの場合は、ドキュメントが検索されます。  検索条件に一致する項目が見つかった場合は、それが自動的に選択されます。  
  
 <xref:Microsoft.Office.Interop.Word.Find> の条件は累積的、つまり、条件は前の検索条件に追加されることに注意することが重要です。  検索の前に、<xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> メソッドを使用して前の検索から書式をクリアします。  
  
#### Selection オブジェクトを使用してテキストを検索するには  
  
1.  検索文字列を変数に代入します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#68](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#68)]
     [!code-vb[Trin_VstcoreWordAutomation#68](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#68)]  
  
2.  前の検索の書式をクリアします。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#69](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#69)]
     [!code-vb[Trin_VstcoreWordAutomation#69](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#69)]  
  
3.  検索を実行し、結果を含むメッセージ ボックスを表示します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#70](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#70)]
     [!code-vb[Trin_VstcoreWordAutomation#70](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#70)]  
  
 このメソッドを使ったサンプル コード全体を次に示します。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#67](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#67)]
 [!code-vb[Trin_VstcoreWordAutomation#67](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#67)]  
  
## Range オブジェクトの使用  
 <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを使用すると、ユーザー インターフェイスに何も表示せずにテキストを検索することができます。  <xref:Microsoft.Office.Interop.Word.Find> オブジェクトは、検索条件に一致するテキストが検出された場合は **True** を返し、検出されない場合は **False** を返します。  また、テキストが検出された場合は、検索条件を突き合わせる <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを再定義します。  
  
#### Range オブジェクトを使用してテキストを検索するには  
  
1.  ドキュメントの 2 番目の段落で構成される <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを定義します。  
  
     次のコード例はドキュメント レベルのカスタマイズで使用できます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#72](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#72)]
     [!code-vb[Trin_VstcoreWordAutomation#72](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#72)]  
  
     次のコード例は VSTO アドインで使用できます。  この例ではアクティブ ドキュメントを使用します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#72)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#72)]  
  
2.  <xref:Microsoft.Office.Interop.Word.Range> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.Find%2A> プロパティを使用して、まず、既存の書式オプションをクリアし、次に文字列 **fine me** を検索します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#73](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#73)]
     [!code-vb[Trin_VstcoreWordAutomation#73](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#73)]  
  
3.  メッセージ ボックスに検索結果を表示し、<xref:Microsoft.Office.Interop.Word.Range> を選択してそれが見えるようにします。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#74](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#74)]
     [!code-vb[Trin_VstcoreWordAutomation#74](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#74)]  
  
     検索が失敗すると 2 番目の段落が選択されます。検索が成功すれば、検索結果が表示されます。  
  
 次の例は、ドキュメント レベルのカスタマイズのコード全体を示しています。  この例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#71](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#71)]
 [!code-vb[Trin_VstcoreWordAutomation#71](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#71)]  
  
 次の例は、VSTO アドインのコード全体を示しています。  この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#71)]
 [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#71)]  
  
## ドキュメント内のテキストを検索し、置換する  
 次のコードでは、現在の選択項目を検索し、出現した文字列 **find me** をすべて文字列 **Found** で置き換えます。  
  
#### ドキュメント内のテキストを検索し、置換するには  
  
1.  プロジェクトの `ThisDocument` または `ThisAddIn` クラスに次のコード例を追加します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#75](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#75)]
     [!code-vb[Trin_VstcoreWordAutomation#75](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#75)]  
  
     <xref:Microsoft.Office.Interop.Word.Find> クラスには <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> メソッドがあり、<xref:Microsoft.Office.Interop.Word.Replacement> クラスにも独自の <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> メソッドがあります。  検索と置換の操作を実行している場合は、両方のオブジェクトの ClearFormatting メソッドを使用する必要があります。  <xref:Microsoft.Office.Interop.Word.Find> オブジェクトでのみこのメソッドを使用すると、置換テキストで予想外の結果になる可能性があります。  
  
2.  検出された各項目を置換するには、<xref:Microsoft.Office.Interop.Word.Find> オブジェクトの <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> メソッドを使用します。  置換する項目を指定するには、*Replace* パラメーターを使用します。  このパラメーターには、次の <xref:Microsoft.Office.Interop.Word.WdReplace> 値のいずれかを指定できます。  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> は検出されたすべての項目を置換します。  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> 検出されたどの項目も置換しません。  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> は検出された最初の項目を置換します。  
  
## 参照  
 [方法: プログラムによって Word の検索オプションを設定する](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [方法: 文書で見つかった項目をプログラムによってループする](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [方法: プログラムによって文書に複数の範囲を定義して選択する](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [方法: プログラムによって検索後に選択範囲を復元する](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  