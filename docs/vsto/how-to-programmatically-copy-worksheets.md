---
title: "方法: プログラムによってワークシートをコピー |Microsoft ドキュメント"
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
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fe8b289dd30ea44331a2ae0c63dd451da8969369
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-copy-worksheets"></a>方法: プログラムによってワークシートをコピーする
  ワークシートのコピーを作成し、ブック内の既存のワークシートの前または後に挿入できます。 ワークシートの挿入先を指定しない場合は、新しいブックが作成され、そこに新しいワークシートが格納されます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  プログラミングによってワークシートをコピーした場合でも、エンド ユーザーが手動でワークシートをコピーした場合でも、新しいワークシートの背後にはコードが存在せず、新しいワークシート上のコントロールは機能しません。 これは、新しくコピーしたワークシートが <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトであって、<xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目ではないためです。 Windows フォーム コントロールおよびホスト コントロールは、ホスト項目にのみ追加できます。 詳細については、「 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)」を参照してください。  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズで、コピーしたワークシートをブックに追加するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> メソッドを使用して、作業中のブック内の 1 番目のワークシートをコピーし、そのコピーを 3 番目のシートの後に挿入します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>VSTO アドインで、コピーしたワークシートをブックに追加するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> メソッドを使用して、作業中のブック内の 1 番目のワークシートをコピーし、そのコピーを 3 番目のシートの後に挿入します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="see-also"></a>参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [方法: プログラムによって新しいワークシートをブックに追加](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [方法: プログラムによってブックからワークシートを削除](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [方法: プログラムによってワークシートを選択します。](../vsto/how-to-programmatically-select-worksheets.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  