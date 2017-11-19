---
title: "方法: プログラムによって文書を閉じる |Microsoft ドキュメント"
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
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
ms.assetid: d5bee1dc-63d1-4307-828f-b7b077e20fb9
caps.latest.revision: "55"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0cc6b310e0c376afb7e0e9a7ade5b91cb4bbb77d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-close-documents"></a>方法: プログラムによって文書を閉じる
  作業中の文書を閉じたり、文書を指定して閉じたりすることができます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="closing-the-active-document"></a>作業中の文書を閉じる  
 作業中の文書を閉じる手順には、ドキュメント レベルのカスタマイズでの手順と VSTO アドインでの手順の 2 つがあります。  
  
#### <a name="to-close-the-active-document-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズで作業中の文書を閉じるには  
  
1.  プロジェクトの <xref:Microsoft.Office.Tools.Word.Document.Close%2A> クラスの `ThisDocument` メソッドを呼び出して、カスタマイズに関連付けられた文書を閉じます。 次のコード例を使用するには、 `ThisDocument` クラスからコードを実行します。  
  
    > [!NOTE]  
    >  この例では、変更内容を保存したりユーザーにメッセージを表示したりせずに文書を閉じるために、 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> パラメーターに *F:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges* 値を渡します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]  
  
#### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>VSTO アドインで作業中の文書を閉じるには  
  
1.  <xref:Microsoft.Office.Interop.Word._Document.Close%2A> プロパティの <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> メソッドを呼び出して、作業中の文書を閉じます。 次のコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
    > [!NOTE]  
    >  この例では、変更内容を保存したりユーザーにメッセージを表示したりせずに文書を閉じるために、 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> パラメーターに *F:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges* 値を渡します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]  
  
## <a name="closing-a-document-that-you-specify-by-name"></a>名前を指定して文書を閉じる  
 名前を指定して文書を閉じる方法は、VSTO アドインとドキュメント レベルのカスタマイズで同じです。  
  
#### <a name="to-close-a-document-that-you-specify-by-name"></a>名前を指定して文書を閉じるには  
  
1.  <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> コレクションへの引数として文書名を指定して、 <xref:Microsoft.Office.Interop.Word._Document.Close%2A> メソッドを呼び出します。 次のコード例は、Word で「 **NewDocument** 」という名前の文書が開いていることを前提としています。  
  
    > [!NOTE]  
    >  この例では、変更内容を保存したりユーザーにメッセージを表示したりせずに文書を閉じるために、 <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> パラメーターに *F:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges* 値を渡します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって既存のドキュメントを開く](../vsto/how-to-programmatically-open-existing-documents.md)   
 [方法: プログラムによって文書を保存](../vsto/how-to-programmatically-save-documents.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  