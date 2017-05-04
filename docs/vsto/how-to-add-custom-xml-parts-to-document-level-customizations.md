---
title: "方法 : ドキュメント レベルのカスタマイズにカスタム XML 部分を追加する | Microsoft Docs"
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
  - "ドキュメント レベルのカスタマイズ [Visual Studio での Office 開発]、カスタム XML 部分"
  - "Office ドキュメント [Visual Studio での Office 開発]、カスタム XML 部分"
  - "Word [Visual Studio での Office 開発]、カスタム XML 部分"
  - "Excel [Visual Studio での Office 開発]、カスタム XML 部分"
  - "カスタム XML 部分 [Visual Studio での Office 開発]、追加"
  - "ドキュメント [Visual Studio での Office 開発]、カスタム XML 部分"
ms.assetid: e305a3d6-3a0e-4e72-ab8c-6a87a3590068
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 方法 : ドキュメント レベルのカスタマイズにカスタム XML 部分を追加する
  ドキュメント レベルのカスタマイズにカスタム XML 部分を作成すると、Microsoft Office Excel ブックまたは Microsoft Office Word 文書に XML データを格納できます。 詳細については、「[カスタム XML 部分の概要](../vsto/custom-xml-parts-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Visual Studio では、Microsoft Office PowerPoint のドキュメント レベルのプロジェクトは提供していません。 VSTO アドインを使用した PowerPoint プレゼンテーションへのカスタム XML 部分の追加について詳しくは、「[方法: VSTO アドインを使用してドキュメントにカスタム XML 部分を追加する](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)」をご覧ください。  
  
### カスタム XML 部分を Excel ブックに追加するには  
  
1.  ブックの <xref:Microsoft.Office.Core.CustomXMLParts> コレクションに、新しい <xref:Microsoft.Office.Core.CustomXMLPart> オブジェクトを追加します。<xref:Microsoft.Office.Core.CustomXMLPart> にはブックに格納する XML 文字列が含まれています。  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelDocLevel/CS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelDocLevel/VB/ThisWorkbook.vb#1)]  
  
2.  Excel のドキュメント レベルのプロジェクト内の `ThisWorkbook` クラスに `AddCustomXmlPartToWorkbook` メソッドを追加します。  
  
3.  プロジェクトの他のコードからメソッドを呼び出します。 たとえば、ユーザーがブックを開いたときにカスタム XML 部分を作成するには、このメソッドを `ThisWorkbook_Startup` イベント ハンドラーから呼び出します。  
  
### カスタム XML 部分を Word ドキュメントに追加するには  
  
1.  ドキュメントの <xref:Microsoft.Office.Core.CustomXMLParts> コレクションに、新しい <xref:Microsoft.Office.Core.CustomXMLPart> オブジェクトを追加します。<xref:Microsoft.Office.Core.CustomXMLPart> にはドキュメントに格納する XML 文字列が含まれています。  
  
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordDocLevel/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordDocLevel/VB/ThisDocument.vb#1)]  
  
2.  Word のドキュメント レベルのプロジェクト内の `ThisDocument` クラスに `AddCustomXmlPartToDocument` メソッドを追加します。  
  
3.  プロジェクトの他のコードからメソッドを呼び出します。 たとえば、ユーザーが文書を開いたときにカスタム XML 部分を作成するには、このメソッドを `ThisDocument_Startup` イベント ハンドラーから呼び出します。  
  
## 信頼性の高いプログラミング  
 わかりやすくするために、この例では、メソッドでローカル変数として定義されている XML 文字列を使用しています。 通常は、ファイルやデータベースなどの外部ソースから XML を取得する必要があります。  
  
## 参照  
 [カスタム XML 部分の概要](../vsto/custom-xml-parts-overview.md)   
 [方法: VSTO アドインを使用してドキュメントにカスタム XML 部分を追加する](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
  