---
title: '方法: プログラムで定義し、ドキュメントで範囲を選択します'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b6922613c7a1493d5b40b807166281ae11eb04d6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835501"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>方法: プログラムで定義し、ドキュメントで範囲を選択します
  Microsoft Office Word 文書内に範囲を定義するには、<xref:Microsoft.Office.Interop.Word.Range> オブジェクトを使用します。 使用してなど、さまざまな方法でドキュメント全体を選択することができます、<xref:Microsoft.Office.Interop.Word.Range.Select%2A>のメソッド、<xref:Microsoft.Office.Interop.Word.Range>オブジェクト、またはの Content プロパティを使用して、<xref:Microsoft.Office.Tools.Word.Document>クラス (ドキュメント レベルのカスタマイズ)、または<xref:Microsoft.Office.Interop.Word.Document>クラス (で、VSTO アドインの場合)。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="define-a-range"></a>範囲を定義します。  
 次の使用例は、作業中の文書の最初の 7 文字 (非印刷文字を含む) で構成される新しい <xref:Microsoft.Office.Interop.Word.Range> オブジェクトの作成方法を示します。 次に、範囲内のテキストを選択します。  
  
### <a name="to-define-a-range-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズで範囲を定義するには  
  
1.  文書に範囲を追加するには、<xref:Microsoft.Office.Tools.Word.Document> クラスの <xref:Microsoft.Office.Tools.Word.Document.Range%2A> メソッドに開始文字と終了文字を渡します。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]  
  
### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>VSTO アドインを使用して範囲を定義するには  
  
1.  文書に範囲を追加するには、<xref:Microsoft.Office.Interop.Word.Document> クラスの <xref:Microsoft.Office.Interop.Word._Document.Range%2A> メソッドに開始文字と終了文字を渡します。 作業中の文書に範囲を追加するコード例を次に示します。 このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]  
  
## <a name="select-a-range-in-a-document-level-customization"></a>ドキュメント レベル カスタマイズで範囲を選択します。  
 次の例は、<xref:Microsoft.Office.Interop.Word.Range> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.Select%2A> メソッドを使用して、または <xref:Microsoft.Office.Tools.Word.Document> クラスの <xref:Microsoft.Office.Tools.Word.Document.Content%2A> プロパティを使用して文書全体を選択する方法を示しています。  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Select メソッドを使用して文書全体を範囲として選択するには  
  
1.  文書全体を含む <xref:Microsoft.Office.Interop.Word.Range> の <xref:Microsoft.Office.Interop.Word.Range.Select%2A> メソッドを使用します。 次のコード例を使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Content プロパティを使用して文書全体を範囲として選択するには  
  
1. <xref:Microsoft.Office.Tools.Word.Document.Content%2A> プロパティを使用して、文書全体を含む範囲を定義します。  
  
    [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]  
  
   また、他のオブジェクトのメソッドとプロパティを使用して範囲を定義することもできます。  
  
### <a name="to-select-a-sentence-in-the-active-document"></a>作業中の文書の文を選択するには  
  
1. <xref:Microsoft.Office.Interop.Word.Sentences> コレクション使用して範囲を設定します。 選択する文のインデックスを使用します。  
  
    [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]  
  
   文を選択するもう 1 つの方法として、範囲の開始値と終了値を手動で設定する方法があります。  
  
### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>開始値と終了値を手動で設定して文を選択するには  
  
1.  範囲変数を作成します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]  
  
2.  ドキュメント内に少なくとも 2 つの文があるかを確認設定、*開始*と*エンド*の範囲、および、選択範囲の引数。  
  
     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]  
  
## <a name="select-a-range-by-using-a-vsto-add-in"></a>VSTO アドインを使用して範囲を選択します。  
 次の例は、<xref:Microsoft.Office.Interop.Word.Range> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.Select%2A> メソッドを使用して、または <xref:Microsoft.Office.Interop.Word.Document> クラスの <xref:Microsoft.Office.Interop.Word._Document.Content%2A> プロパティを使用して文書全体を選択する方法を示しています。  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Select メソッドを使用して文書全体を範囲として選択するには  
  
1.  文書全体を含む <xref:Microsoft.Office.Interop.Word.Range> の <xref:Microsoft.Office.Interop.Word.Range.Select%2A> メソッドを使用します。 次のコード例では、作業中の文書の内容を選択します。 このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Content プロパティを使用して文書全体を範囲として選択するには  
  
1. <xref:Microsoft.Office.Interop.Word._Document.Content%2A> プロパティを使用して、文書全体を含む範囲を定義します。  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]  
  
   また、他のオブジェクトのメソッドとプロパティを使用して範囲を定義することもできます。  
  
### <a name="to-select-a-sentence-in-the-active-document"></a>作業中の文書の文を選択するには  
  
1. <xref:Microsoft.Office.Interop.Word.Sentences> コレクション使用して範囲を設定します。 選択する文のインデックスを使用します。  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]  
  
   文を選択するもう 1 つの方法として、範囲の開始値と終了値を手動で設定する方法があります。  
  
### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>開始値と終了値を手動で設定して文を選択するには  
  
1.  範囲変数を作成します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]  
  
2.  ドキュメント内に少なくとも 2 つの文があるかを確認設定、*開始*と*エンド*の範囲、および、選択範囲の引数。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]  
  
## <a name="see-also"></a>関連項目  
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [方法: プログラムによってドキュメント内の範囲を拡張します。](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [方法: 範囲の先頭と末尾の文字をプログラムで取得します。](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [方法: プログラムによってドキュメント内の範囲を拡張します。](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [方法: プログラムによって Word のドキュメント内の範囲をリセットします。](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [方法: プログラムまたはドキュメント内の選択範囲を折りたたむ](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [方法: プログラムから除外する段落記号の範囲を作成するときに](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
