---
title: "方法: VSTO アドインを使用してドキュメントにカスタム XML 部分を追加する | Microsoft Docs"
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
  - "アドイン [Visual Studio での Office 開発]、カスタム XML 部分"
  - "Office ドキュメント [Visual Studio での Office 開発]、カスタム XML 部分"
  - "Word [Visual Studio での Office 開発]、カスタム XML 部分"
  - "PowerPoint [Visual Studio での Office 開発]、カスタム XML 部分"
  - "Excel [Visual Studio での Office 開発]、カスタム XML 部分"
  - "カスタム XML 部分 [Visual Studio での Office 開発]、追加"
  - "ドキュメント [Visual Studio での Office 開発]、カスタム XML 部分"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発]、カスタム XML 部分"
ms.assetid: 872d2beb-193b-49f9-9a7b-dcebab91a73b
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 方法: VSTO アドインを使用してドキュメントにカスタム XML 部分を追加する
  VSTO アドインでカスタム XML 部分を作成することにより、次のタイプのドキュメントに XML データを格納できます。  
  
-   Microsoft Office Excel ブック。  
  
-   Microsoft Office Word ドキュメント。  
  
-   Microsoft Office PowerPoint プレゼンテーション。  
  
 詳細については、「[カスタム XML 部分の概要](../vsto/custom-xml-parts-overview.md)」を参照してください。  
  
 **対象:** このトピックの情報は、Excel、PowerPoint、および Word のアプリケーション レベルのプロジェクトに適用されます。 詳細については、「[Office アプリケーションおよびプロジェクト タイプ別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
### カスタム XML 部分を Excel ブックに追加するには  
  
1.  ブックの <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> コレクションに、新しい <xref:Microsoft.Office.Core.CustomXMLPart> オブジェクトを追加します。<xref:Microsoft.Office.Core.CustomXMLPart> にはブックに格納する XML 文字列が含まれています。  
  
     次のコード例は、指定したブックにカスタム XML 部分を追加します。  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Excel の VSTO アドイン プロジェクトの `ThisAddIn` クラスに、`AddCustomXmlPartToWorkbook` メソッドを追加します。  
  
3.  プロジェクトの他のコードからメソッドを呼び出します。 たとえば、ユーザーがブックを開いたときにカスタム XML 部分を作成するには、<xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> イベントのイベント ハンドラーからメソッドを呼び出します。  
  
### カスタム XML 部分を Word ドキュメントに追加するには  
  
1.  ドキュメントの <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> コレクションに、新しい <xref:Microsoft.Office.Core.CustomXMLPart> オブジェクトを追加します。<xref:Microsoft.Office.Core.CustomXMLPart> にはドキュメントに格納する XML 文字列が含まれています。  
  
     次のコード例は、指定したドキュメントにカスタム XML 部分を追加します。  
  
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Word の VSTO アドイン プロジェクトの `ThisAddIn` クラスに、`AddCustomXmlPartToDocument` メソッドを追加します。  
  
3.  プロジェクトの他のコードからメソッドを呼び出します。 たとえば、ユーザーがドキュメントを開いたときにカスタム XML 部分を作成するには、<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> イベントのイベント ハンドラーからメソッドを呼び出します。  
  
### PowerPoint プレゼンテーションにカスタム XML 部分を追加するには  
  
1.  プレゼンテーションの <xref:Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts%2A> コレクションに、新しい <xref:Microsoft.Office.Core.CustomXMLPart> オブジェクトを追加します。<xref:Microsoft.Office.Core.CustomXMLPart> にはプレゼンテーションに格納する XML 文字列が含まれています。  
  
     次のコード例は、指定したプレゼンテーションにカスタム XML 部分を追加します。  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartPowerPointAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartPowerPointAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  PowerPoint の VSTO アドイン プロジェクトの `ThisAddIn` クラスに、`AddCustomXmlPartToPresentation` メソッドを追加します。  
  
3.  プロジェクトの他のコードからメソッドを呼び出します。 たとえば、ユーザーがプレゼンテーションを開いたときにカスタム XML 部分を作成するには、<xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen> イベントのイベント ハンドラーからメソッドを呼び出します。  
  
## 信頼性の高いプログラミング  
 わかりやすくするために、この例では、メソッドでローカル変数として定義されている XML 文字列を使用しています。 通常は、ファイルやデータベースなどの外部ソースから XML を取得する必要があります。  
  
## 参照  
 [カスタム XML 部分の概要](../vsto/custom-xml-parts-overview.md)   
 [方法 : ドキュメント レベルのカスタマイズにカスタム XML 部分を追加する](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  