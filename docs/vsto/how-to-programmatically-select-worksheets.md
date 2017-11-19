---
title: "方法: プログラムによってワークシートを選択する |Microsoft ドキュメント"
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
- worksheets, selecting
- Excel projects, selecting worksheets
ms.assetid: 9e7cdb11-e825-4c9f-abcd-d46fd20dc5e0
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2dcd68c96d06613e67b4fdafafecdbbff780eae4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-select-worksheets"></a>方法: プログラムによってワークシートを選択する
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> メソッドは指定されたオブジェクトを選択します。これにより、ユーザーの選択が新しいオブジェクトに移動します。 ユーザーの選択を変更せずにフォーカスをオブジェクトに移動する場合は、<xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> メソッドを使用します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 VSTO アドインで既存のワークシートを選択する場合、または、ドキュメント レベルのカスタマイズでワークシートが実行時に作成された場合は、Excel ブックの Excel  <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションを使用してこれにアクセスする必要があります。それ以外の場合は、<xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目に直接アクセスできます。  
  
## <a name="using-the-worksheet-host-item"></a>ワークシートのホスト項目を使用する  
 ドキュメント レベルのカスタマイズで次のコードを追加**Sheet1.vb**または**Sheet1.cs**です。  
  
#### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>ホスト項目を使用してブック内の最初のワークシートを選択するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> の `Sheet1` メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Excel ブックの Sheets コレクションの使用  
 Excel の <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションを使用して、ワークシートにアクセスします。  
  
#### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Excel ブックの Sheets コレクションを使用して、ブック内の最初のワークシートを選択するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションの <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> メソッドを呼び出して、作業中のブックの最初のワークシートを選択します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]  
  
## <a name="see-also"></a>関連項目  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: プログラムによってワークシートを印刷します。](../vsto/how-to-programmatically-print-worksheets.md)   
 [方法: プログラムによってブックからワークシートを削除](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [方法: プログラムによってワークシートを非表示](../vsto/how-to-programmatically-hide-worksheets.md)   
 [方法: プログラムによってワークシートを保護します。](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  