---
title: "方法: プログラムによって新しいワークシートをブックに追加 |Microsoft ドキュメント"
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
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
ms.assetid: 19f0d815-51b2-406c-9f36-34aa0ec16b4a
caps.latest.revision: "52"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: cbd8928b8bcf3e782533f068aaaee8085e331f9c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>方法: プログラムを使用して新しいワークシートをブックに追加する
  プログラムによってワークシートを作成し、そのワークシートをブック内のワークシートのコレクションに追加できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズで、新しいワークシートをブックに追加するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> コレクションの <xref:Microsoft.Office.Interop.Excel.Sheets> メソッドを使用します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]  
  
     新しいワークシートはネイティブの <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトであり、ホスト項目ではありません。 <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目を追加するには、デザイン時にワークシートを追加する必要があります。  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>VSTO アドインで、新しいワークシートをブックに追加するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> コレクションの <xref:Microsoft.Office.Interop.Excel.Sheets> メソッドを使用します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]  
  
     新しいワークシートはネイティブの <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトであり、ホスト項目ではありません。 ネイティブの <xref:Microsoft.Office.Tools.Excel.Worksheet> オブジェクトから <xref:Microsoft.Office.Interop.Excel.Worksheet> ホスト項目を生成することもできます。 詳細については、「 [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [方法: プログラムによってブックからワークシートを削除](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [方法: プログラムによってワークシートを選択します。](../vsto/how-to-programmatically-select-worksheets.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  