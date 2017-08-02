---
title: "方法 : カスタム ドキュメント プロパティを作成および変更する"
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
  - "カスタム ドキュメント プロパティ"
  - "ドキュメント [Visual Studio での Office 開発]、プロパティ"
  - "ドキュメント プロパティ [Visual Studio での Office 開発]"
ms.assetid: 99d9dfaf-891f-4f3b-a580-67362afdaf34
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 方法 : カスタム ドキュメント プロパティを作成および変更する
  上記の Microsoft Office アプリケーションは、ドキュメントで保存される組み込みのプロパティを提供します。 さらに、ドキュメントで保存する追加情報がある場合は、カスタム ドキュメント プロパティを作成し、変更することができます。  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 ドキュメントの CustomDocumentProperties プロパティを使用して、カスタム プロパティを操作します。 たとえば、Microsoft Office Excel のドキュメント レベルのプロジェクトでは、`ThisWorkbook` クラスの <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> プロパティを使用します。 Excel の VSTO アドイン プロジェクトでは、<xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトの <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> プロパティを使用します。 これらのプロパティは、<xref:Microsoft.Office.Core.DocumentProperty> オブジェクトのコレクションである <xref:Microsoft.Office.Core.DocumentProperties> オブジェクトを返します。 このコレクションの `Item` プロパティを使用すると、名前またはコレクション内のインデックスに基づいて特定のプロパティを取得できます。  
  
 次の例は、Excel のドキュメント レベルのカスタマイズでカスタム プロパティを追加し、値を割り当てる方法を示します。  
  
 ![ビデオへのリンク](~/data-tools/media/playvideo.gif "ビデオへのリンク") 関連するビデオ デモについては、「[操作方法: Microsoft Word のカスタム ドキュメント プロパティにアクセスして操作する](http://go.microsoft.com/fwlink/?LinkId=136772)」を参照してください。  
  
## 使用例  
 [!code-csharp[Trin_VstcoreProgramming#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#6)]
 [!code-vb[Trin_VstcoreProgramming#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#6)]  
  
## 信頼性の高いプログラミング  
 未定義の `Value` プロパティにアクセスしようとすると、例外が発生します。  
  
## 参照  
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)   
 [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)   
 [方法 : ドキュメント プロパティの読み込みと書き込みを行う](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  