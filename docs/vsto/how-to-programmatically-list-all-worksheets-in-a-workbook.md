---
title: "方法: プログラムによってブック内のすべてのワークシートを一覧表示 |Microsoft ドキュメント"
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
- workbooks, listing worksheets
- worksheets, listing
ms.assetid: 38b63d1d-6047-44e8-b089-c576c6179e4a
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9a4478e7fb0895e15be5d239da541b7c9fab7e44
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>方法: プログラムによってブック内のすべてのワークシートを一覧表示する
  <xref:Microsoft.Office.Interop.Excel.Workbook> クラスには、<xref:Microsoft.Office.Interop.Excel.Worksheets> オブジェクトが用意されています。 このオブジェクトには、ブック内のすべての <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトのコレクションが含まれます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズで、ブック内の既存のワークシートを一覧表示するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Worksheets> コレクションを反復処理し、各ワークシートの名前を、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールからオフセットされるセルに送信します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]  
  
### <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>VSTO アドインで、ブック内の既存のワークシートを一覧表示するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Worksheets> コレクションを反復処理し、各ワークシートの名前を、<xref:Microsoft.Office.Interop.Excel.Range> オブジェクトからオフセットされるセルに送信します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: プログラムによって新しいワークシートをブックに追加](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [方法: プログラムによってブック内のワークシートを移動](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)  
  
  