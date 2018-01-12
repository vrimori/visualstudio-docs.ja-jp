---
title: "方法: プログラムによって格納および Excel の範囲に日付値を取得 |Microsoft ドキュメント"
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
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 589079a593400549a69940fc42d1cf25fcab8826
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>方法: プログラムによって Excel の範囲内のデータの値を格納および取得する
  保存し、で値を取得できる、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールまたはネイティブな Excel 範囲オブジェクト。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Visual Studio での Office 開発ツールの使用範囲内には 1/1/1900 以降にある日付の値を格納する場合は、OLE オートメーション (OA) 形式で格納されます。 使用する必要があります、 <xref:System.DateTime.FromOADate%2A> OLE オートメーション (OA) 日付の値を取得します。 日付が 1900 年 1 月 1 日より前の場合は、文字列として格納されます。  
  
> [!NOTE]  
>  Excel の日付は 1900 年の最初の 2 か月の OLE オートメーション日付によって異なります。 いる場合も違い、 **1904**オプションはオンにします。 次のコード例では、これらの相違点は対応していません。  
  
## <a name="using-a-namedrange-control"></a>NamedRange コントロールを使用します。  
  
-   この例は、ドキュメント レベルのカスタマイズがあります。 次のコードではなく、シート クラスに配置する必要があります、`ThisWorkbook`クラスです。  
  
#### <a name="to-store-a-date-value-in-a-named-range"></a>名前付き範囲に日付値を格納するには  
  
1.  作成、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールのセルで**A1**です。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]  
  
2.  値として今日の日付を設定`NamedRange1`です。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]  
  
#### <a name="to-retrieve-a-date-value-from-a-named-range"></a>名前付き範囲から、日付の値を取得するには  
  
1.  日付の値を取得`NamedRange1`です。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]  
  
## <a name="using-native-excel-ranges"></a>ネイティブ Excel の範囲を使用します。  
  
#### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>ネイティブな Excel 範囲オブジェクトに日付値を格納するには  
  
1.  作成、<xref:Microsoft.Office.Interop.Excel.Range>セルを表す**A1**です。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]  
  
2.  値として今日の日付を設定`rng`です。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]  
  
#### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>ネイティブな Excel 範囲オブジェクトから、日付の値を取得するには  
  
1.  日付の値を取得`rng`です。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]  
  
## <a name="see-also"></a>参照  
 [範囲の使用](../vsto/working-with-ranges.md)   
 [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [方法: プログラムによってワークシートの範囲をコード内を参照してください](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [方法: ワークシートに NamedRange コントロールを追加します。](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  