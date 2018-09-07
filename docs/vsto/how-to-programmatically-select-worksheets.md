---
title: '方法: プログラムによってワークシートを選択します。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 09e477d802b9d92ca4f9e1cd3a532145ad0e68a0
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673774"
---
# <a name="how-to-programmatically-select-worksheets"></a>方法: プログラムによってワークシートを選択します。
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> メソッドは指定されたオブジェクトを選択します。これにより、ユーザーの選択が新しいオブジェクトに移動します。 ユーザーの選択を変更せずにフォーカスをオブジェクトに移動する場合は、<xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> メソッドを使用します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 VSTO アドインで既存のワークシートを選択するか、ワークシートは、ドキュメント レベルのカスタマイズの実行時に作成されている場合、Excel を使用してアクセスする必要があります<xref:Microsoft.Office.Interop.Excel.Sheets>Excel ブックのコレクション、にアクセスする場合は、<xref:Microsoft.Office.Tools.Excel.Worksheet>ホスト項目に直接します。  
  
## <a name="use-the-worksheet-host-item"></a>ワークシート ホスト項目を使用します。  
 ドキュメント レベルのカスタマイズで次のコードを追加*Sheet1.vb*または*Sheet1.cs*します。  
  
### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>ホスト項目を使用してブック内の最初のワークシートを選択するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> の `Sheet1` メソッドを呼び出します。  
  
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
 [方法: プログラムによってブックからワークシートを削除](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [方法: プログラムによってワークシートを非表示](../vsto/how-to-programmatically-hide-worksheets.md)   
 [方法: プログラムによってワークシートを保護します。](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  