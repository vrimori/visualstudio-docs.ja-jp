---
title: '方法: プログラムによって文書でテキストの書式設定'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2e0cc5c9e42d3de2b0b5ed34664639b70b31abb3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835277"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>方法: プログラムによって文書でテキストの書式設定
  <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを使用することにより、Microsoft Office Word 文書のテキストの書式を設定できます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 次の例では、文書内の最初の段落を選択し、フォント サイズ、フォント名、およびアラインメントを変更します。 次に、範囲を選択し、コードの次のセクションを実行する前に一時停止するためのメッセージ ボックスを表示します。 次のセクションでの元に戻すメソッドを呼び出して、 <xref:Microsoft.Office.Tools.Word.Document> (ドキュメント レベルのカスタマイズ) のホスト項目または<xref:Microsoft.Office.Interop.Word.Document>クラス (VSTO アドインが) 3 回です。 標準のインデント スタイルを適用し、メッセージ ボックスを表示してコードを一時停止します。 最後に、 <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> メソッドを 1 回呼び出し、メッセージ ボックスを表示します。  
  
## <a name="document-level-customization-example"></a>ドキュメント レベルのカスタマイズ例  
  
### <a name="to-format-text-using-a-document-level-customization"></a>ドキュメント レベルのカスタマイズを使用してテキストの書式を設定するには  
  
1.  次のコード例はドキュメント レベルのカスタマイズで使用できます。 このコードを使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]  
  
## <a name="vsto-add-in-example"></a>VSTO アドインの例  
  
### <a name="to-format-text-using-a-vsto-add-in"></a>VSTO アドインを使用してテキストを書式設定するには  
  
1.  次の例は VSTO アドインで使用できます。 この例ではアクティブ ドキュメントを使用します。 このコードを使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムで定義し、ドキュメントで範囲を選択します](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [方法: プログラムによって Word 文書にテキストを挿入します。](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [方法: プログラムを検索して、文書内のテキストを置換](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
