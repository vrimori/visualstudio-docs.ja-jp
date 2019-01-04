---
title: '方法: 範囲の先頭と末尾の文字をプログラムで取得します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9891e54986cd829c92ab3f5a5ad3a81590cf1474
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871201"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>方法: 範囲の先頭と末尾の文字をプログラムで取得します。
  この例では、範囲の開始位置と終了位置の文字位置を取得する方法を示します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズ内の範囲の先頭と末尾の文字を取得するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Range> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.Start%2A> プロパティおよび <xref:Microsoft.Office.Interop.Word.Range.End%2A> プロパティの値を取得します。 次のコード例では、ドキュメントの 2 番目の文の開始位置と終了位置を取得します。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>VSTO アドインを使用して、範囲の先頭と末尾の文字を取得するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Range.Start%2A> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.End%2A> プロパティおよび <xref:Microsoft.Office.Interop.Word.Range> プロパティの値を取得します。 次のコード例では、アクティブなドキュメントの 2 番目の文の開始位置と終了位置を取得します。 このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムで定義し、ドキュメントで範囲を選択します](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [方法: プログラムによってドキュメント内の範囲を拡張します。](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [方法: プログラムによって Word のドキュメント内の範囲をリセットします。](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [方法: プログラムまたはドキュメント内の選択範囲を折りたたむ](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [方法: プログラムから除外する段落記号の範囲を作成するときに](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [方法: プログラムによって文書内の文字をカウントします。](../vsto/how-to-programmatically-count-characters-in-documents.md)  
