---
title: '方法: プログラムによってワークシート内の行をグループ化します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5249edccaed24dbdc6eb42b5da3e78825f1a2053
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874410"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>方法: プログラムによってワークシート内の行をグループ化します。
  1 つ以上の行をグループ化することができます。 ワークシート内でグループを作成するには、使用、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールまたはネイティブな Excel 範囲オブジェクト。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>NamedRange コントロールを使用します。  
 追加する場合、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールをデザイン時にドキュメント レベル プロジェクトに、プログラムでグループを作成するコントロールを使用することができます。 次の例である 3 つ<xref:Microsoft.Office.Tools.Excel.NamedRange>同じワークシート上のコントロール: `data2001`、 `data2002`、および`dataAll`します。 各名前付き範囲は、ワークシートの行全体を指します。  
  
### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>ワークシートに NamedRange コントロールのグループを作成するには  
  
1.  呼び出して 3 つの名前付き範囲をグループ化、<xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A>各範囲のメソッド。 このコードは、 `ThisWorkbook` クラスではなく、シート クラスに配置する必要があります。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  グループを解除するには、行を呼び出し、<xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A>メソッド。  
  
## <a name="use-native-excel-ranges"></a>ネイティブの Excel の範囲を使用して、  
 コードでは、という名前の 3 つの Excel の範囲であると想定`data2001`、 `data2002`、および`dataAll`ワークシートにします。  
  
### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>ワークシート内で Excel の範囲のグループを作成するには  
  
1.  呼び出して 3 つの名前付き範囲をグループ化、<xref:Microsoft.Office.Interop.Excel.Range.Group%2A>各範囲のメソッド。 次の例である 3 つ<xref:Microsoft.Office.Interop.Excel.Range>という名前のコントロール`data2001`、 `data2002`、および`dataAll`同じワークシートにします。 各名前付き範囲は、ワークシートの行全体を指します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  グループを解除するには、行を呼び出し、<xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A>メソッド。  
  
## <a name="see-also"></a>関連項目  
 [ワークシートを操作します。](../vsto/working-with-worksheets.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [方法: ワークシートに NamedRange コントロールを追加します。](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
