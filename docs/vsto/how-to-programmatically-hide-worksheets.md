---
title: '方法: プログラムによってワークシートを非表示'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a60a0189af5608496e1f0f415a2d668e896af8e3
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673630"
---
# <a name="how-to-programmatically-hide-worksheets"></a>方法: プログラムによってワークシートを非表示
  ブック内の任意のワークシートの表示と非表示を切り替えることができます。 ワークシートを非表示にするには、Worksheet ホスト項目を使用するか、ブックの Sheets コレクションを使用してワークシートにアクセスします。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-the-worksheet-host-item"></a>ワークシート ホスト項目を使用します。  
 デザイン時にドキュメント レベルのカスタマイズでワークシートが追加された場合は、 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> プロパティを使用して特定のワークシートを非表示にします。  
  
### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Worksheet ホスト項目を使用してワークシートを非表示にするには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> ホスト項目の `Sheet1` プロパティを列挙値 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> に設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Excel ブックの Sheets コレクションを使用して、  
 次の場合は、Microsoft Office Excel の <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションを使用してワークシートにアクセスします。  
  
-   VSTO アドインでワークシートを非表示にするには。  
  
-   非表示にするワークシートがドキュメント レベルのカスタマイズで実行時に作成された場合。  
  
### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Excel ブックの Sheets コレクションを使用してワークシートを非表示にするには  
  
1.  ワークシートの <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> プロパティを列挙値 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> に設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]  
  
## <a name="see-also"></a>関連項目  
 [ワークシートを操作します。](../vsto/working-with-worksheets.md)   
 [方法: プログラムによってブックからワークシートを削除](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [方法: プログラムによってブック内のワークシートを移動](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [方法: プログラムによってワークシートを保護します。](../vsto/how-to-programmatically-protect-worksheets.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)  
  