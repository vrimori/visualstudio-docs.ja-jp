---
title: '方法: プログラムによって文書内のテキストにコメントを追加'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ca0d15ee69bb58aae765c03c1233a78bfeeb119c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671922"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>方法: プログラムによって文書内のテキストにコメントを追加
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
 [方法: プログラムによって文書からすべてのコメントを削除](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Document ホスト項目](../vsto/document-host-item.md)  
  
  