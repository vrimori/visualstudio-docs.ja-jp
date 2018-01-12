---
title: "方法: プログラムによって文書内のテキストを書式設定 |Microsoft ドキュメント"
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
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 602c9e8f3e846f38a50c39c34f5d08f47f74d155
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-format-text-in-documents"></a>方法: プログラムによって文書内のテキストに書式を設定する
  <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを使用することにより、Microsoft Office Word 文書のテキストの書式を設定できます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 次の例では、文書内の最初の段落を選択し、フォント サイズ、フォント名、およびアラインメントを変更します。 次に、範囲を選択し、コードの次のセクションを実行する前に一時停止するためのメッセージ ボックスを表示します。 次のセクションで、元に戻すのメソッドを呼び出して、<xref:Microsoft.Office.Tools.Word.Document>ホスト項目 (ドキュメント レベルのカスタマイズ)、または<xref:Microsoft.Office.Interop.Word.Document>クラス (VSTO アドインで提供) 3 回です。 標準のインデント スタイルを適用し、メッセージ ボックスを表示してコードを一時停止します。 最後に、 <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> メソッドを 1 回呼び出し、メッセージ ボックスを表示します。  
  
## <a name="document-level-customization-example"></a>ドキュメント レベルのカスタマイズの例  
  
#### <a name="to-format-text-using-a-document-level-customization"></a>ドキュメント レベルのカスタマイズを使用してテキストの書式を設定するには  
  
1.  次のコード例はドキュメント レベルのカスタマイズで使用できます。 このコードを使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]  
  
## <a name="vsto-add-in-example"></a>VSTO アドインの例  
  
#### <a name="to-format-text-using-a-vsto-add-in"></a>VSTO アドインを使用してテキストを書式設定するには  
  
1.  次の例は VSTO アドインで使用できます。 この例ではアクティブ ドキュメントを使用します。 このコードを使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]  
  
## <a name="see-also"></a>参照  
 [方法: プログラムによってを定義し、ドキュメントで範囲を選択](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [方法: プログラムによって Word 文書にテキストを挿入](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [方法: プログラムによって文書内のテキストを検索および置換する](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  