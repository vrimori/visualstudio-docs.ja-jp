---
title: '方法: 最近使用ブック ファイルをプログラムで一覧表示'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 850dc26b9a5f270b3806d9623795535d34cf8f4b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989634"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>方法: 最近使用ブック ファイルをプログラムで一覧表示
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>プロパティは、最近使用したファイルの Microsoft Office Excel リストに表示されるすべてのファイルの名前を含むコレクションを返します。 リストの長さは、保持する、ユーザーが選択したファイルの数によって異なります。 範囲内で結果を表示することができます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Range オブジェクトの一覧を最近使用したブックを  
  
1.  最近使ったファイルの一覧をループしを基準とするセルの名前を表示、<xref:Microsoft.Office.Interop.Excel.Range>オブジェクト。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>関連項目  
 [ブックを操作します。](../vsto/working-with-workbooks.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
