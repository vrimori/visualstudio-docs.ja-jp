---
title: '方法: プログラムによってリスト最近使用したブック ファイル |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: c2d9c333b6d96329abec3fd52ecaa5da1cf97c74
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>方法: 最近使用したブック ファイルをプログラムによって一覧表示する
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>プロパティ最近使ったファイルの Microsoft Office Excel リストに表示されるすべてのファイルの名前を含むコレクションを返します。 リストの長さは、保持する、ユーザーが選択したファイルの数によって異なります。 範囲の結果を表示することができます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Range オブジェクトで使用されるブックを最近を一覧表示するには  
  
1.  最近使ったファイルの一覧をループし、に対して相対的なセルに名前を表示、<xref:Microsoft.Office.Interop.Excel.Range>オブジェクト。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>関連項目  
 [ブックの操作](../vsto/working-with-workbooks.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  