---
title: "方法: プログラムによって文書および文書の一部を保護する |Microsoft ドキュメント"
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
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
ms.assetid: af8390fc-c4c7-48c7-94b8-4fedbaac0757
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2d37fc65a094aa3f6733045ca6ba9380bc522741
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>方法: プログラムによって文書および文書の一部を保護する
  Microsoft Office Word 文書に保護を追加して、ユーザーによるドキュメントの編集を防止できます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ドキュメントの特定の領域を例外としてマークし、指定したユーザーに対し、ドキュメントのその領域の編集のみを許可することもできます。 たとえば、特定のブックマークを除くドキュメント全体を保護できます。 必要に応じてパスワードを追加し、パスワードを知らないユーザーに対し、ドキュメント保護の解除を禁止できます。  
  
> [!NOTE]  
>  次の例では、パスワード保護を使用しません。ただし、ドキュメント保護を追加するときに、パスワードの使用を検討することもできます。 詳しくは、「 [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md)」にあるドキュメント保護のサンプルをご覧ください。  
  
 コンテンツ コントロールを使用してドキュメントの一部を保護することもできます。 詳細については、「 [How to: Protect Parts of Documents by Using Content Controls](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)」を参照してください。  
  
## <a name="protecting-a-document-that-is-part-of-a-document-level-customization"></a>ドキュメント レベルのカスタマイズの一部であるドキュメントの保護  
  
#### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>ドキュメント レベルのカスタマイズの一部であるドキュメントを保護するには  
  
1.  プロジェクトの <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> クラスの `ThisDocument` メソッドを呼び出します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
#### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>ブックマーク コントロールをドキュメント保護から除外するには  
  
1.  <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> メソッドを使用してドキュメント全体を保護します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
2.  ドキュメント保護から `Bookmark1` を除外します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]  
  
### <a name="compiling-the-code"></a>コードのコンパイル  
 これらのコード例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。 これらのコード例は、コードが表示されるドキュメントに <xref:Microsoft.Office.Tools.Word.Bookmark> という名前の既存の `Bookmark1` コントロールが存在していることを前提としています。  
  
## <a name="protecting-a-document-by-using-an-vsto-add-in"></a>VSTO アドインを使用したドキュメントの保護  
  
#### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>アプリケーション レベルの VSTO アドインを使用してドキュメントを保護するには  
  
1.  保護する <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> の <xref:Microsoft.Office.Interop.Word.Document> メソッドを呼び出します。  
  
     アクティブなドキュメントを保護するコード例を次に示します。 このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]  
  
## <a name="see-also"></a>参照  
 [ドキュメント レベルのソリューションでドキュメントの保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Office ドキュメントのパスワード保護](../vsto/password-protection-on-office-documents.md)   
 [方法: アクセス許可の制限のドキュメントの背後に実行するようにコードを許可します。](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)  
  
  