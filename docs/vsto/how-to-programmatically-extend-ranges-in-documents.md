---
title: '方法: プログラムによってドキュメント内の範囲を拡張'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bd8eff41b0e76816114e9c634f5ad61b6db58baf
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672233"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>方法: プログラムによって拡張の範囲のドキュメントで
  Microsoft Office Word ドキュメントで <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを定義した後、その始点と終点を <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> メソッドと <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> メソッドを使用して変更します。 <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A>と<xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A>メソッドが同じ 2 つの引数を受け取ります*単位*と*カウント*します。 *カウント*引数は、移動するユニットの数と*単位*引数は、次のいずれかを指定できます<xref:Microsoft.Office.Interop.Word.WdUnits>値。  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 次の例では、7 文字の範囲を定義します。 その後、開始位置を元の開始位置から 7 文字後に移動します。 範囲の終了位置も開始位置より 7 文字後にあるため、結果はゼロ文字からなる範囲になります。 このコードは続いて、終了位置を現在の終了位置から 7 文字後に移動します。  
  
## <a name="to-extend-a-range"></a>範囲を拡張するには  
  
1.  文字の範囲を定義します。 詳細については、次を参照してください。[方法: プログラムで定義し、ドキュメントで範囲を選択](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)します。  
  
     次のコード例はドキュメント レベルのカスタマイズで使用できます。  
  
     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]  
  
     次のコード例は VSTO アドインで使用できます。 この例ではアクティブ ドキュメントを使用します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]  
  
2.  <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range> メソッドを使用して、範囲の開始位置を移動します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]  
  
3.  <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range> メソッドを使用して、範囲の終了位置を移動します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]  
  
## <a name="document-level-customization-code"></a>ドキュメント レベルのカスタマイズ コード  
  
### <a name="to-extend-a-range-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズで範囲を拡張するには  
  
1.  次の例は、ドキュメント レベルのカスタマイズのコード全体を示しています。 このコードを使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]  
  
## <a name="vsto-add-in-code"></a>VSTO アドイン コード  
  
### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>アプリケーション レベルの VSTO アドインで範囲を拡張するには  
  
1.  次の例は、VSTO アドインのコード全体を示しています。 このコードを使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって Word のドキュメント内の範囲をリセット](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [方法: プログラムによって範囲またはドキュメント内の選択を折りたたむ](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [方法: プログラムで定義し、ドキュメントで範囲を選択します](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [方法: 範囲の先頭と末尾の文字をプログラムで取得します。](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [方法: 範囲を作成するときにプログラムによって段落記号を除外します。](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  