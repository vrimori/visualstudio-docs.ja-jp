---
title: "方法: VSTO アドインを使用してドキュメントにカスタム XML 部分を追加 |Microsoft ドキュメント"
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
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
ms.assetid: 872d2beb-193b-49f9-9a7b-dcebab91a73b
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e851c0dcdbb3ed86dcf4a303cc1ad26b65035bc8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>方法: VSTO アドインを使用してドキュメントにカスタム XML 部分を追加する
  VSTO アドインでカスタム XML 部分を作成することにより、次のタイプのドキュメントに XML データを格納できます。  
  
-   Microsoft Office Excel ブック。  
  
-   Microsoft Office Word ドキュメント。  
  
-   Microsoft Office PowerPoint プレゼンテーション。  
  
 詳細については、「 [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md)」を参照してください。  
  
 **対象:** このトピックの情報は、Excel、PowerPoint、および Word のアプリケーション レベルのプロジェクトに適用されます。 詳細については、「 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>カスタム XML 部分を Excel ブックに追加するには  
  
1.  ブックの <xref:Microsoft.Office.Core.CustomXMLPart> コレクションに、新しい <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> オブジェクトを追加します。 <xref:Microsoft.Office.Core.CustomXMLPart> にはブックに格納する XML 文字列が含まれています。  
  
     次のコード例は、指定したブックにカスタム XML 部分を追加します。  
  
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]  
  
2.  Excel の VSTO アドイン プロジェクトの `AddCustomXmlPartToWorkbook` クラスに、 `ThisAddIn` メソッドを追加します。  
  
3.  プロジェクトの他のコードからメソッドを呼び出します。 たとえば、ユーザーがブックを開いたときにカスタム XML 部分を作成するには、 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> イベントのイベント ハンドラーからメソッドを呼び出します。  
  
### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>カスタム XML 部分を Word ドキュメントに追加するには  
  
1.  ドキュメントの <xref:Microsoft.Office.Core.CustomXMLPart> コレクションに、新しい <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> オブジェクトを追加します。 <xref:Microsoft.Office.Core.CustomXMLPart> にはドキュメントに格納する XML 文字列が含まれています。  
  
     次のコード例は、指定したドキュメントにカスタム XML 部分を追加します。  
  
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]  
  
2.  Word の VSTO アドイン プロジェクトの `AddCustomXmlPartToDocument` クラスに、 `ThisAddIn` メソッドを追加します。  
  
3.  プロジェクトの他のコードからメソッドを呼び出します。 たとえば、ユーザーがドキュメントを開いたときにカスタム XML 部分を作成するには、 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> イベントのイベント ハンドラーからメソッドを呼び出します。  
  
### <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>PowerPoint プレゼンテーションにカスタム XML 部分を追加するには  
  
1.  プレゼンテーションの <xref:Microsoft.Office.Core.CustomXMLPart> コレクションに、新しい <xref:Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts%2A> オブジェクトを追加します。 <xref:Microsoft.Office.Core.CustomXMLPart> にはプレゼンテーションに格納する XML 文字列が含まれています。  
  
     次のコード例は、指定したプレゼンテーションにカスタム XML 部分を追加します。  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]  
  
2.  PowerPoint の VSTO アドイン プロジェクトの `AddCustomXmlPartToPresentation` クラスに、 `ThisAddIn` メソッドを追加します。  
  
3.  プロジェクトの他のコードからメソッドを呼び出します。 たとえば、ユーザーがプレゼンテーションを開いたときにカスタム XML 部分を作成するには、 <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen> イベントのイベント ハンドラーからメソッドを呼び出します。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 わかりやすくするために、この例では、メソッドでローカル変数として定義されている XML 文字列を使用しています。 通常は、ファイルやデータベースなどの外部ソースから XML を取得する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md)   
 [方法: ドキュメント レベルのカスタマイズにカスタム XML 部分を追加する](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  