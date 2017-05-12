---
title: "方法 : ドキュメント プロパティの読み込みと書き込みを行う"
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
  - "Word [Visual Studio での Office 開発]、ドキュメント プロパティ"
  - "ドキュメント [Visual Studio での Office 開発]、プロパティ"
  - "ドキュメント プロパティ [Visual Studio での Office 開発]"
  - "Excel [Visual Studio での Office 開発]、ドキュメント プロパティ"
ms.assetid: e9ef9fa3-36b9-48fb-8148-f5152463c03c
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 方法 : ドキュメント プロパティの読み込みと書き込みを行う
  ドキュメント プロパティをドキュメントと共に保存できます。 Office アプリケーションには、作成者、タイトル、件名など、多数の組み込みプロパティが用意されています。 このトピックでは、Microsoft Office Excel および Microsoft Office Word でドキュメント プロパティを設定する方法について説明します。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.png "ビデオへのリンク") 関連のビデオ デモについては、「[操作方法: Microsoft Word のカスタム ドキュメント プロパティにアクセスして操作する](http://go.microsoft.com/fwlink/?LinkId=136772)」を参照してください。  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## Excel のドキュメント プロパティの設定  
 Excel の組み込みプロパティを操作するには、次のプロパティを使用します。  
  
-   ドキュメント レベルのプロジェクトでは、`ThisWorkbook` クラスの <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> プロパティを使用します。  
  
-   VSTO アドイン プロジェクトでは、<xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトの <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> プロパティを使用します。  
  
 これらのプロパティは、<xref:Microsoft.Office.Core.DocumentProperties> オブジェクトのコレクションである <xref:Microsoft.Office.Core.DocumentProperty> オブジェクトを返します。 このコレクションの `Item` プロパティを使用すると、名前またはコレクション内のインデックスに基づいて特定のプロパティを取得できます。  
  
 次のコード例は、ドキュメント レベルのプロジェクトで組み込みの **Revision Number** プロパティを変更する方法を示しています。  
  
#### Excel の Revision Number プロパティを変更するには  
  
1.  組み込みのドキュメント プロパティを変数に代入します。  
  
     [!code-csharp[Trin_VstcoreProgramming#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#7)]
     [!code-vb[Trin_VstcoreProgramming#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#7)]  
  
2.  `Revision Number` プロパティの値を 1 つインクリメントします。  
  
     [!code-csharp[Trin_VstcoreProgramming#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#8)]
     [!code-vb[Trin_VstcoreProgramming#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#8)]  
  
## Word のドキュメント プロパティの設定  
 Word の組み込みプロパティを操作するには、次のプロパティを使用します。  
  
-   ドキュメント レベルのプロジェクトでは、`ThisDocument` クラスの <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> プロパティを使用します。  
  
-   VSTO アドイン プロジェクトでは、<xref:Microsoft.Office.Interop.Word.Document> オブジェクトの <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> プロパティを使用します。  
  
 これらのプロパティは、<xref:Microsoft.Office.Core.DocumentProperties> オブジェクトのコレクションである <xref:Microsoft.Office.Core.DocumentProperty> オブジェクトを返します。 このコレクションの `Item` プロパティを使用すると、名前またはコレクション内のインデックスに基づいて特定のプロパティを取得できます。  
  
 次のコード例は、ドキュメント レベルのプロジェクトで組み込みの **Subject** プロパティを変更する方法を示しています。  
  
#### Subject プロパティを変更するには  
  
1.  組み込みのドキュメント プロパティを変数に代入します。  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#1)]  
  
2.  `Subject` プロパティを「Whitepaper」に変更します。  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#2)]  
  
## 信頼性の高いプログラミング  
 これらの例では、Excel の場合はドキュメント レベルのプロジェクトの `ThisWorkbook` クラス、Word の場合はドキュメント レベルのプロジェクトの `ThisDocument` クラスにそれぞれコードを記述していることを前提としています。  
  
 Word、Excel、およびそれらのオブジェクトを操作する場合でも、Microsoft Office では使用可能な組み込みドキュメント プロパティの一覧が提供されます。 未定義のプロパティにアクセスしようとすると、例外が発生します。  
  
## 参照  
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)   
 [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)   
 [方法 : カスタム ドキュメント プロパティを作成および変更する](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  