---
title: '方法: プログラムによってワークシートを選択します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2ecb6872d56d4dc7f54f3ef73e0f8dafed06d2e6
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863120"
---
# <a name="how-to-programmatically-select-worksheets"></a>方法: プログラムによってワークシートを選択します。
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> メソッドは指定されたオブジェクトを選択します。これにより、ユーザーの選択が新しいオブジェクトに移動します。 ユーザーの選択を変更せずにフォーカスをオブジェクトに移動する場合は、<xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> メソッドを使用します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 VSTO アドインで既存のワークシートを選択するか、ワークシートは、ドキュメント レベルのカスタマイズの実行時に作成されている場合、Excel を使用してアクセスする必要があります<xref:Microsoft.Office.Interop.Excel.Sheets>Excel ブックのコレクション、にアクセスする場合は、<xref:Microsoft.Office.Tools.Excel.Worksheet>ホスト項目に直接します。  
  
## <a name="use-the-worksheet-host-item"></a>ワークシート ホスト項目を使用します。  
 ドキュメント レベルのカスタマイズで次のコードを追加*Sheet1.vb*または*Sheet1.cs*します。  
  
### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>ホスト項目を使用してブック内の最初のワークシートを選択するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> の `Sheet1`メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Excel ブックの sheets コレクションを使用して、  
 Excel の <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションを使用して、ワークシートにアクセスします。  
  
### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Excel ブックの Sheets コレクションを使用して、ブック内の最初のワークシートを選択するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションの <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> メソッドを呼び出して、作業中のブックの最初のワークシートを選択します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]  
  
## <a name="see-also"></a>関連項目  
 [ワークシートを操作します。](../vsto/working-with-worksheets.md)   
 [方法: プログラムによってワークシートを印刷します。](../vsto/how-to-programmatically-print-worksheets.md)   
 [方法: プログラムによってブックからワークシートを削除します。](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [方法: プログラムによってワークシートを非表示します。](../vsto/how-to-programmatically-hide-worksheets.md)   
 [方法: プログラムによってワークシートを保護します。](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
