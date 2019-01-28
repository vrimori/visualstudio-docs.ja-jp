---
title: '方法: プログラムによって格納および Excel の範囲内の日付値を取得'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24155f9ea8703d7089714a9b0adce9310612a4ea
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872717"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>方法: プログラムによって格納および Excel の範囲内の日付値を取得
  格納して、値を取得、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールまたはネイティブな Excel 範囲オブジェクト。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Visual Studio での Office 開発ツールの使用範囲内には 1/1/1900 以降にある日付の値を格納する場合は、OLE オートメーション (OA) 形式で格納されます。 使用する必要があります、 <xref:System.DateTime.FromOADate%2A> OLE オートメーション (OA) 日付の値を取得します。 日付が 1/1/1900 より前の場合は、文字列として格納されます。  
  
> [!NOTE]  
>  Excel の日付は 1900 年の最初の 2 か月間の OLE オートメーション日付によって異なります。 違いが場合、 **1904**オプションをオンにします。 次のコード例では、これらの違いは対応していません。  
  
## <a name="use-a-namedrange-control"></a>NamedRange コントロールを使用します。  
  
-   この例では、ドキュメント レベルのカスタマイズです。 次のコードではなく、シート クラスに配置する必要があります、`ThisWorkbook`クラス。  
  
### <a name="to-store-a-date-value-in-a-named-range"></a>名前付き範囲に日付の値を格納するには  
  
1.  作成、<xref:Microsoft.Office.Tools.Excel.NamedRange>セルにあるコントロール**A1**します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]  
  
2.  今日の日付を値として設定`NamedRange1`します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]  
  
### <a name="to-retrieve-a-date-value-from-a-named-range"></a>名前付き範囲から日付値を取得するには  
  
1.  日付値を取得`NamedRange1`します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]  
  
## <a name="use-native-excel-ranges"></a>ネイティブの Excel の範囲を使用して、  
  
### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>ネイティブな Excel 範囲オブジェクトに日付の値を格納するには  
  
1.  作成、<xref:Microsoft.Office.Interop.Excel.Range>セルを表す**A1**します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]  
  
2.  今日の日付を値として設定`rng`します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]  
  
### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>ネイティブな Excel 範囲オブジェクトから日付値を取得するには  
  
1.  日付値を取得`rng`します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]  
  
## <a name="see-also"></a>関連項目  
 [範囲を操作します。](../vsto/working-with-ranges.md)   
 [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [方法: コード内でワークシートの範囲をプログラムで参照してください。](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [方法: ワークシートに NamedRange コントロールを追加します。](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
