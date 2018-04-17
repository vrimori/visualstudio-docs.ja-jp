---
title: '方法: プログラムによって開始と終了文字の範囲を取得 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: a79112e80885dfd64b85a90125ea059277725d33
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>方法: 範囲の開始文字と終了文字をプログラムによって取得する
  この例では、範囲の開始位置と終了位置の文字位置を取得する方法を示します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズ内の範囲の先頭と末尾の文字を取得するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Range.Start%2A> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.End%2A> プロパティおよび <xref:Microsoft.Office.Interop.Word.Range> プロパティの値を取得します。 次のコード例では、ドキュメントの 2 番目の文の開始位置と終了位置を取得します。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-an-vsto-add-in"></a>VSTO アドインを使用して、範囲の先頭と末尾の文字を取得するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Range.Start%2A> オブジェクトの <xref:Microsoft.Office.Interop.Word.Range.End%2A> プロパティおよび <xref:Microsoft.Office.Interop.Word.Range> プロパティの値を取得します。 次のコード例では、アクティブなドキュメントの 2 番目の文の開始位置と終了位置を取得します。 このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによってを定義し、ドキュメントで範囲を選択](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [方法: プログラムによってドキュメント内の範囲を拡張します。](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [方法: プログラムによってリセット Word 文書の範囲](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [方法: プログラムによって範囲を縮小またはドキュメントの選択](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [方法: 範囲を作成するときにプログラムによって段落記号を除外します。](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [方法: プログラムによって文書内の文字数をカウントする](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  