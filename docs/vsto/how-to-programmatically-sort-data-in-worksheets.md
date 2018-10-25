---
title: '方法: プログラムによってワークシートのデータの並べ替え'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 179cf5fab5a1b2690cb4b46160f7a5c3342fe7bc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914217"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>方法: プログラムによってワークシートのデータの並べ替え
  実行時にワークシートの範囲およびリストに含まれているデータを並べ替えることができます。 次のコードは、複数の列で構成される `Fruits` という名前の範囲を、最初の列のデータを基に並べ替え、次に 2 番目の列のデータを基に並べ替えます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="sort-data-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズのデータを並べ替える  
  
### <a name="to-sort-data-in-a-namedrange-control"></a>NamedRange コントロール内のデータを並べ替えるには  
  
1. <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールの <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> メソッドを呼び出します。 次のコード例では、ワークシートに `Fruits` という名前の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールが必要です。 このコードは、 `ThisWorkbook` クラスではなく、シート クラスに配置する必要があります。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
    [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]  
  
   次のコードを配置*Sheet1.vb*または*Sheet1.cs*データを並べ替える、<xref:Microsoft.Office.Tools.Excel.ListObject>コントロール。 このコードでは、`Sheet1` という名前のワークシートに、`fruitList` という名前の <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールがあることを前提としています。  
  
### <a name="to-sort-data-in-a-listobject-control"></a>ListObject コントロール内のデータを並べ替えるには  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject> ホスト コントロールの <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> プロパティの <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]  
  
## <a name="sort-data-in-a-vsto-add-in"></a>VSTO アドインのデータを並べ替える  
  
### <a name="to-sort-data-in-a-native-range"></a>ネイティブな範囲でデータを並べ替えるには  
  
1.  ネイティブな Excel <xref:Microsoft.Office.Interop.Excel.Range> コントロールの <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> メソッドを呼び出します。 次のコード例では、ワークシートに `Fruits` という名前のネイティブな Excel コントロールが必要です。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]  
  
### <a name="to-sort-data-in-a-listobject-control"></a>ListObject コントロール内のデータを並べ替えるには  
  
1.  ネイティブな Excel <xref:Microsoft.Office.Interop.Excel.ListObject> コントロールの <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> プロパティの <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> メソッドを呼び出します。 次の例は、作業中のワークシートに `fruitList` という名前のネイティブな Excel <xref:Microsoft.Office.Interop.Excel.ListObject> コントロールがあることを前提としています。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]  
  
## <a name="see-also"></a>関連項目  
 [ワークシートを操作します。](../vsto/working-with-worksheets.md)   
 [方法: プログラムによって自動的に増分するデータ範囲を入力](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [方法: プログラムによってコード内でワークシートの範囲を参照](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [方法: プログラムによってブック内の範囲にスタイルを適用](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  