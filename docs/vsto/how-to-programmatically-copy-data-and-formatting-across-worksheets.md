---
title: '方法: データとワークシート間で書式設定をプログラムによってコピーします。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: babf55cd7728734e6ab6575c960a2b821f510154
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087868"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>方法: データとワークシート間で書式設定をプログラムによってコピーします。
  使用して、ブック内の他のすべてのシートの 1 つのシート上の範囲からのデータをコピーすることができます、<xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A>メソッド。 範囲を指定し、データ、書式設定、またはその両方をコピーするかどうか。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 この例では名前付き`rangeData`ワークシート内で。  
  
## <a name="see-also"></a>関連項目  
 [ワークシートを操作します。](../vsto/working-with-worksheets.md)   
 [方法: プログラムで新しいワークシートをブックに追加します。](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [方法: 選択したセルを含むワークシートの行の書式設定をプログラムで変更します。](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
