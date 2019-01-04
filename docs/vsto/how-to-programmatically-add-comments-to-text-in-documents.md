---
title: '方法: プログラムによって文書内のテキストにコメントを追加します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 677f0ba2cf02f4dd62759ea5f125c91290dc0762
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857028"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>方法: プログラムによって文書内のテキストにコメントを追加します。
  ドキュメント クラスのコメント プロパティは、Microsoft Office Word 文書にテキストの範囲にコメントを追加します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 次の例は、文書の最初の段落にコメントを追加します。  
  
## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズで、新しいコメントをテキストに追加するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> プロパティの <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> メソッドを呼び出し、範囲とコメントのテキストを入力します。 次のコード例を使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]  
  
## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>VSTO アドイン内のテキストに新しいコメントを追加するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> プロパティの <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> メソッドを呼び出し、範囲とコメントのテキストを入力します。  
  
     作業中の文書にコメントを追加するコード例を次に示します。 このコード例を使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 Word によってコメントに追加されるユーザーの頭文字を変更するには、 <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> プロパティを使用します。  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって文書からすべてのコメントを削除します。](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Document ホスト項目](../vsto/document-host-item.md)  
