---
title: "方法: プログラムによってワークシートのデータを並べ替える |Microsoft ドキュメント"
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
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
ms.assetid: 2fbc6e63-02ea-4624-8d6f-bed60e06c61e
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 211a357095290f8f8d608d01c093cd373c7525ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>方法: プログラムを使用してワークシート内のデータを並べ替える
  実行時にワークシートの範囲およびリストに含まれているデータを並べ替えることができます。 次のコードは、複数の列で構成される `Fruits` という名前の範囲を、最初の列のデータを基に並べ替え、次に 2 番目の列のデータを基に並べ替えます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="sorting-data-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズにおけるデータの並べ替え  
  
#### <a name="to-sort-data-in-a-namedrange-control"></a>NamedRange コントロール内のデータを並べ替えるには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールの <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> メソッドを呼び出します。 次のコード例では、ワークシートに `Fruits` という名前の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールが必要です。 このコードは、 `ThisWorkbook` クラスではなく、シート クラスに配置する必要があります。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]  
  
 次のコードを Sheet1.vb または Sheet1.cs に配置して、<xref:Microsoft.Office.Tools.Excel.ListObject> コントロール内のデータを並べ替えます。 このコードでは、`Sheet1` という名前のワークシートに、`fruitList` という名前の <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールがあることを前提としています。  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>ListObject コントロール内のデータを並べ替えるには  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject> ホスト コントロールの <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> プロパティの <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]  
  
## <a name="sorting-data-in-a-vsto-add-in"></a>VSTO アドイン内のデータの並べ替え  
  
#### <a name="to-sort-data-in-a-native-range"></a>ネイティブな範囲でデータを並べ替えるには  
  
1.  ネイティブな Excel <xref:Microsoft.Office.Interop.Excel.Range> コントロールの <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> メソッドを呼び出します。 次のコード例では、ワークシートに `Fruits` という名前のネイティブな Excel コントロールが必要です。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>ListObject コントロール内のデータを並べ替えるには  
  
1.  ネイティブな Excel <xref:Microsoft.Office.Interop.Excel.ListObject> コントロールの <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> プロパティの <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> メソッドを呼び出します。 次の例は、作業中のワークシートに `fruitList` という名前のネイティブな Excel <xref:Microsoft.Office.Interop.Excel.ListObject> コントロールがあることを前提としています。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]  
  
## <a name="see-also"></a>関連項目  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: 増分するデータを自動的にプログラムで塗りつぶし範囲](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [方法: プログラムによってワークシートの範囲をコード内を参照してください](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [方法: プログラムによってブック内の範囲にスタイルを適用](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  