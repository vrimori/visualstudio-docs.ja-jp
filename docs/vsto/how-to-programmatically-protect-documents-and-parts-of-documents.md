---
title: "方法: プログラムによって文書および文書の一部を保護する"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ドキュメント保護"
  - "ドキュメント [Visual Studio での Office 開発]、ドキュメント保護"
  - "Word 文書、保護"
ms.assetid: af8390fc-c4c7-48c7-94b8-4fedbaac0757
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 方法: プログラムによって文書および文書の一部を保護する
  Microsoft Office Word 文書に保護を追加して、ユーザーによるドキュメントの編集を防止できます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ドキュメントの特定の領域を例外としてマークし、指定したユーザーに対し、ドキュメントのその領域の編集のみを許可することもできます。 たとえば、特定のブックマークを除くドキュメント全体を保護できます。 必要に応じてパスワードを追加し、パスワードを知らないユーザーに対し、ドキュメント保護の解除を禁止できます。  
  
> [!NOTE]  
>  次の例では、パスワード保護を使用しません。ただし、ドキュメント保護を追加するときに、パスワードの使用を検討することもできます。 詳しくは、「[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)」にあるドキュメント保護のサンプルをご覧ください。  
  
 コンテンツ コントロールを使用してドキュメントの一部を保護することもできます。 詳細については、「[方法 : コンテンツ コントロールを使用して文書を保護する](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)」を参照してください。  
  
## ドキュメント レベルのカスタマイズの一部であるドキュメントの保護  
  
#### ドキュメント レベルのカスタマイズの一部であるドキュメントを保護するには  
  
1.  プロジェクトの `ThisDocument` クラスの <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
#### ブックマーク コントロールをドキュメント保護から除外するには  
  
1.  <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> メソッドを使用してドキュメント全体を保護します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
2.  ドキュメント保護から `Bookmark1` を除外します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#112](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#112)]
     [!code-vb[Trin_VstcoreWordAutomation#112](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#112)]  
  
### コードのコンパイル  
 これらのコード例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。 これらのコード例は、コードが表示されるドキュメントに `Bookmark1` という名前の既存の <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールが存在していることを前提としています。  
  
## VSTO アドインを使用したドキュメントの保護  
  
#### アプリケーション レベルの VSTO アドインを使用してドキュメントを保護するには  
  
1.  保護する <xref:Microsoft.Office.Interop.Word.Document> の <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> メソッドを呼び出します。  
  
     アクティブなドキュメントを保護するコード例を次に示します。 このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#111)]  
  
## 参照  
 [ドキュメント レベルのソリューションにおけるドキュメントの保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Office ドキュメントのパスワード保護](../vsto/password-protection-on-office-documents.md)   
 [方法 : アクセス許可が制限されたドキュメントでの分離コードの実行を許可する](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [方法 : Word 文書に Bookmark コントロールを追加する](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)  
  
  