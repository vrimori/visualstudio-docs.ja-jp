---
title: '方法: 文書内の文字をプログラムでカウント |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4ae05466c871b51d790f1031755be062806fc120
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>方法: プログラムによって文書内の文字数をカウントする
  ドキュメント内の最初の文字は、挿入ポイントを表す文字位置 0 に位置します。 最後の文字位置は、ドキュメント内の文字数の合計と同じになります。 <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> コレクションの <xref:Microsoft.Office.Interop.Word.Characters> のプロパティを使用して、ドキュメント内の文字数を特定することができます。  
  
 スペース、段落記号、通常は表示されないその他の文字を含む、ドキュメント内のすべての文字がカウントされます。 新規作成された空白のドキュメントでも、段落記号が含まれているため、1 文字が返されます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズで文字数を表示するには  
  
1.  ドキュメント全体を選択します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]  
  
2.  メッセージ ボックスにドキュメント内の文字数が表示されます。  
  
     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]  
  
### <a name="to-display-the-number-of-characters-in-an-vsto-add-in"></a>VSTO アドインで文字数を表示するには  
  
1.  ドキュメント全体を選択します。 以下の例ではアクティブ ドキュメントが選ばれています。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]  
  
2.  メッセージ ボックスにドキュメント内の文字数が表示されます。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって開始と終了文字の範囲を取得](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [方法: プログラムによって文書に複数の範囲を定義して選択する](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
  
  