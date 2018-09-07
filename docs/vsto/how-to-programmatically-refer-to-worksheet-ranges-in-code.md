---
title: '方法: プログラムによってコード内でワークシートの範囲を参照'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 608ce006ccc34330631da8d4c947405b027f1a1f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672782"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>方法: プログラムによってコード内でワークシートの範囲を参照
  内容を参照する同様のプロセスを使用して、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールまたはネイティブな Excel 範囲オブジェクト。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>NamedRange コントロールを使用します。  
 次の例では、追加、<xref:Microsoft.Office.Tools.Excel.NamedRange>ワークシートにし、範囲内のセルにテキストを追加します。  
  
### <a name="to-refer-to-a-namedrange-control"></a>NamedRange コントロールを参照するには  
  
1.  文字列を割り当てる、<xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>のプロパティ、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロール。 このコードは、 `ThisWorkbook` クラスではなく、シート クラスに配置する必要があります。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="use-native-excel-ranges"></a>ネイティブの Excel の範囲を使用して、  
 次の例では、ワークシートにネイティブな Excel 範囲を追加し、範囲内のセルにテキストを追加します。  
  
### <a name="to-refer-to-a-native-range-object"></a>ネイティブな範囲オブジェクトを参照するには  
  
1.  文字列を割り当てる、<xref:Microsoft.Office.Interop.Excel.Range.Value2%2A>範囲のプロパティ。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>関連項目  
 [範囲を操作します。](../vsto/working-with-ranges.md)   
 [方法: プログラムによってワークシートでスペル チェック](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [方法: プログラムによってブック内の範囲にスタイルを適用](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [方法: プログラムによって自動的に増分するデータ範囲を入力](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [方法: プログラムによってワークシートの範囲内のテキストの検索](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  