---
title: '方法: プログラムによってワークシートを印刷します。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c1e473baccd6e4bb4de1c36d8888082baf40034b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876643"
---
# <a name="how-to-programmatically-print-worksheets"></a>方法: プログラムによってワークシートを印刷します。
  ブック内のワークシートはすべて印刷できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="print-a-worksheet-in-a-document-level-customization"></a>ドキュメント レベル カスタマイズでワークシートを印刷します。  
  
### <a name="to-print-a-worksheet"></a>ワークシートを印刷するには  
  
1. `Sheet1` の <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> メソッドを呼び出します。印刷部数は 2 部で、印刷前に文書をプレビューします。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]  
  
   <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>メソッドでは、指定されたオブジェクトを表示することができます、**印刷プレビュー**ウィンドウ。 次のコードでは、`Sheet1` という名前の <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目があることを前提としています。  
  
### <a name="to-preview-a-page-before-printing"></a>印刷する前にページをプレビューするには  
  
1.  ワークシートの <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]  
  
## <a name="print-a-worksheet-in-a-vsto-add-in"></a>VSTO アドインでワークシートを印刷します。  
  
### <a name="to-print-a-worksheet"></a>ワークシートを印刷するには  
  
1. 作業中のワークシートの <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> メソッドを呼び出します。印刷部数は 2 部で、印刷前に文書をプレビューします。  
  
    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]  
  
   <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>メソッドでは、指定されたオブジェクトを表示することができます、**印刷プレビュー**ウィンドウ。  
  
### <a name="to-preview-a-page-before-printing"></a>印刷する前にページをプレビューするには  
  
1.  作業中のワークシートの <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>関連項目  
 [ワークシートを操作します。](../vsto/working-with-worksheets.md)   
 [方法: プログラムによってワークシートでスペル チェック](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  