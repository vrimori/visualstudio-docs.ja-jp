---
title: "方法: プログラムによってワークシートを非表示に |Microsoft ドキュメント"
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
- hidden worksheets
- worksheets, hiding
ms.assetid: 3208f633-137f-47f9-9c9c-2cf8e3c72096
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 54dddd66a1fb9408117f9f3a02102deb13093bce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-hide-worksheets"></a>方法: プログラムによってワークシートを非表示にする
  ブック内の任意のワークシートの表示と非表示を切り替えることができます。 ワークシートを非表示にするには、Worksheet ホスト項目を使用するか、ブックの Sheets コレクションを使用してワークシートにアクセスします。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-the-worksheet-host-item"></a>ワークシートのホスト項目を使用する  
 デザイン時にドキュメント レベルのカスタマイズでワークシートが追加された場合は、 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> プロパティを使用して特定のワークシートを非表示にします。  
  
#### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Worksheet ホスト項目を使用してワークシートを非表示にするには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> ホスト項目の `Sheet1` プロパティを列挙値 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> に設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Excel ブックの Sheets コレクションの使用  
 次の場合は、Microsoft Office Excel の <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションを使用してワークシートにアクセスします。  
  
-   VSTO アドインでワークシートを非表示にする場合。  
  
-   非表示にするワークシートがドキュメント レベルのカスタマイズで実行時に作成された場合。  
  
#### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Excel ブックの Sheets コレクションを使用してワークシートを非表示にするには  
  
1.  ワークシートの <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> プロパティを列挙値 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> に設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]  
  
## <a name="see-also"></a>参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: プログラムによってブックからワークシートを削除](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [方法: プログラムによってブック内のワークシートを移動](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [方法: プログラムによってワークシートを保護します。](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)  
  