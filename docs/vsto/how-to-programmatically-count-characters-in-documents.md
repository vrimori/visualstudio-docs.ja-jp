---
title: '方法: プログラムによって文書内の文字をカウントします。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57babe4379482c4718990bac936c8bc7f930e112
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872626"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>方法: プログラムによって文書内の文字をカウントします。
  ドキュメント内の最初の文字は、挿入ポイントを表す文字位置 0 に位置します。 最後の文字位置は、ドキュメント内の文字数の合計と同じになります。 <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> コレクションの <xref:Microsoft.Office.Interop.Word.Characters> のプロパティを使用して、ドキュメント内の文字数を特定することができます。  
  
 スペース、段落記号、通常は表示されないその他の文字を含む、ドキュメント内のすべての文字がカウントされます。 新規作成された空白のドキュメントでも、段落記号が含まれているため、1 文字が返されます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズで文字数を表示するには  
  
1.  ドキュメント全体を選択します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]  
  
2.  メッセージ ボックスにドキュメント内の文字数が表示されます。  
  
     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]  
  
## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>VSTO アドインで文字数を表示するには  
  
1.  ドキュメント全体を選択します。 以下の例ではアクティブ ドキュメントが選ばれています。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]  
  
2.  メッセージ ボックスにドキュメント内の文字数が表示されます。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]  
  
## <a name="see-also"></a>関連項目  
 [方法: 範囲の先頭と末尾の文字をプログラムで取得します。](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [方法: プログラムで定義し、ドキュメントで範囲を選択します](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
