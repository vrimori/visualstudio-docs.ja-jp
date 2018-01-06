---
title: "方法: プログラムによってリスト最近使用したブック ファイル |Microsoft ドキュメント"
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
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
ms.assetid: 210a3753-4845-4875-b34a-a30d3a1299b3
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 629b27c5947a2744886ac0d3fed8898ece386c6b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>方法: 最近使用したブック ファイルをプログラムによって一覧表示する
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>プロパティ最近使ったファイルの Microsoft Office Excel リストに表示されるすべてのファイルの名前を含むコレクションを返します。 リストの長さは、保持する、ユーザーが選択したファイルの数によって異なります。 範囲の結果を表示することができます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Range オブジェクトで使用されるブックを最近を一覧表示するには  
  
1.  最近使ったファイルの一覧をループし、に対して相対的なセルに名前を表示、<xref:Microsoft.Office.Interop.Excel.Range>オブジェクト。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>参照  
 [ブックの操作](../vsto/working-with-workbooks.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  