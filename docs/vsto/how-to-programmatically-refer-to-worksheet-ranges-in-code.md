---
title: '方法: プログラムによってワークシートの範囲をコード内を参照してください |Microsoft ドキュメント'
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
ms.openlocfilehash: 68845904a349a94df6ee09c05ca262434b847bbc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>方法: プログラムによってコード内でワークシートの範囲を参照する
  内容を参照する同様のプロセスを使用する、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールまたはネイティブな Excel 範囲オブジェクト。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>NamedRange コントロールを使用します。  
 次の例では追加、<xref:Microsoft.Office.Tools.Excel.NamedRange>をワークシートにし、範囲内のセルにテキストを追加します。  
  
#### <a name="to-refer-to-a-namedrange-control"></a>NamedRange コントロールを参照するには  
  
1.  文字列を割り当てる、<xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>のプロパティ、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロール。 このコードは、 `ThisWorkbook` クラスではなく、シート クラスに配置する必要があります。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="using-native-excel-ranges"></a>ネイティブ Excel の範囲を使用します。  
 次の例では、ワークシートにネイティブな Excel 範囲を追加し、範囲内のセルにテキストを追加します。  
  
#### <a name="to-refer-to-a-native-range-object"></a>ネイティブな範囲オブジェクトを参照するには  
  
1.  文字列を割り当てる、<xref:Microsoft.Office.Interop.Excel.Range.Value2%2A>範囲のプロパティです。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>関連項目  
 [範囲の使用](../vsto/working-with-ranges.md)   
 [方法: プログラムによってワークシートでスペル チェック](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [方法: プログラムによってブック内の範囲にスタイルを適用](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [方法: 増分するデータを自動的にプログラムで塗りつぶし範囲](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [方法: プログラムによってワークシートの範囲内のテキストの検索](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  