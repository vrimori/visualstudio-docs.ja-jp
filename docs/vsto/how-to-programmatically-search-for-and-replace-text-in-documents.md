---
title: "方法: プログラムによって検索し、文書内のテキストを置換 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
ms.assetid: a66962f5-eeb9-4dc6-a70f-9039ab437a63
caps.latest.revision: "51"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3ce2298ee213e310409dd904acb342e390cb1db2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-search-for-and-replace-text--in-documents"></a>方法: プログラムによって文書内のテキストを検索および置換する
  <xref:Microsoft.Office.Interop.Word.Find> オブジェクトは <xref:Microsoft.Office.Interop.Word.Selection> および <xref:Microsoft.Office.Interop.Word.Range> オブジェクトの両方のメンバーであり、どちらを使用しても Microsoft Office Word ドキュメント内のテキストを検索できます。 Replace コマンドは、Find コマンドの拡張機能です。  
  
 <xref:Microsoft.Office.Interop.Word.Find> オブジェクトを使用して Microsoft Office Word ドキュメントをループ処理し、特定のテキスト、書式、またはスタイルを検索し、<xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> プロパティを使用して検出された項目を置き換えます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="using-a-selection-object"></a>Selection オブジェクトの使用  
 テキストを検索するために <xref:Microsoft.Office.Interop.Word.Selection> オブジェクトを使用する場合、指定する検索条件は現在選択されているテキストにしか適用されません。 <xref:Microsoft.Office.Interop.Word.Selection> が挿入ポイントの場合は、ドキュメントが検索されます。 検索条件に一致する項目が見つかった場合は、それが自動的に選択されます。  
  
 <xref:Microsoft.Office.Interop.Word.Find> の条件は累積的、つまり、条件は前の検索条件に追加されることに注意することが重要です。 検索の前に、<xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> メソッドを使用して前の検索から書式をクリアします。  
  
#### <a name="to-find-text-using-a-selection-object"></a>Selection オブジェクトを使用してテキストを検索するには  
  
1.  検索文字列を変数に代入します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
     [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]  
  
2.  前の検索の書式をクリアします。  
  
     [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
     [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]  
  
3.  検索を実行し、結果を含むメッセージ ボックスを表示します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
     [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]  
  
 このメソッドを使ったサンプル コード全体を次に示します。  
  
 [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
 [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]  
  
## <a name="using-a-range-object"></a>Range オブジェクトの使用  
 <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを使用すると、ユーザー インターフェイスに何も表示せずにテキストを検索することができます。 <xref:Microsoft.Office.Interop.Word.Find>オブジェクトを返します**True**検索条件に一致するテキストが見つかった場合、 **False**そうでない場合。 また、テキストが検出された場合は、検索条件を突き合わせる <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを再定義します。  
  
#### <a name="to-find-text-using-a-range-object"></a>Range オブジェクトを使用してテキストを検索するには  
  
1.  ドキュメントの 2 番目の段落で構成される <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを定義します。  
  
     次のコード例はドキュメント レベルのカスタマイズで使用できます。  
  
     [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
     [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]  
  
     次のコード例は VSTO アドインで使用できます。 この例ではアクティブ ドキュメントを使用します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]  
  
2.  使用して、<xref:Microsoft.Office.Interop.Word.Range.Find%2A>のプロパティ、<xref:Microsoft.Office.Interop.Word.Range>オブジェクト、まず既存の書式設定オプションをオフにし、文字列を検索**find me」**です。  
  
     [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
     [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]  
  
3.  メッセージ ボックスに検索結果を表示し、<xref:Microsoft.Office.Interop.Word.Range> を選択してそれが見えるようにします。  
  
     [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
     [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]  
  
     検索が失敗すると 2 番目の段落が選択されます。検索が成功すれば、検索結果が表示されます。  
  
 次の例は、ドキュメント レベルのカスタマイズのコード全体を示しています。 この例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。  
  
 [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
 [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]  
  
 次の例は、VSTO アドインのコード全体を示しています。 この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
 [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]  
  
## <a name="searching-for-and-replacing-text-in-documents"></a>ドキュメント内のテキストを検索し、置換する  
 次のコードが現在の選択範囲を検索し、文字列の出現回数は、のすべてに置き換わります**find me」**文字列**Found**です。  
  
#### <a name="to-search-for-and-replace-text-in-documents"></a>ドキュメント内のテキストを検索し、置換するには  
  
1.  プロジェクトの `ThisDocument` または `ThisAddIn` クラスに次のコード例を追加します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]  
  
     <xref:Microsoft.Office.Interop.Word.Find> クラスには <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> メソッドがあり、<xref:Microsoft.Office.Interop.Word.Replacement> クラスにも独自の <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> メソッドがあります。 検索と置換の操作を実行している場合は、両方のオブジェクトの書式のクリア メソッドを使用する必要があります。 <xref:Microsoft.Office.Interop.Word.Find> オブジェクトでのみこのメソッドを使用すると、置換テキストで予想外の結果になる可能性があります。  
  
2.  検出された各項目を置換するには、<xref:Microsoft.Office.Interop.Word.Find> オブジェクトの <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> メソッドを使用します。 置換する項目を指定する、*置換*パラメーター。 このパラメーターには、次の <xref:Microsoft.Office.Interop.Word.WdReplace> 値のいずれかを指定できます。  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> は検出されたすべての項目を置換します。  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> 検出されたどの項目も置換しません。  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> は検出された最初の項目を置換します。  
  
## <a name="see-also"></a>参照  
 [方法: プログラムによって Word の検索オプションを設定](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [方法: 文書で見つかった項目をプログラムによってループ](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [方法: プログラムによってを定義し、ドキュメントで範囲を選択](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [方法: プログラムによって検索後に選択内容を復元](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  