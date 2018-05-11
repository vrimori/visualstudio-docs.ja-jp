---
title: '方法: プログラムによって新しいブックを作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0ba2054258beb762a6b554a49b7a64a77f83dd7a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-create-new-workbooks"></a>方法: プログラムによって新しいブックを作成する
  プログラムによって作成される新しいブックは、<xref:Microsoft.Office.Tools.Excel.Workbook> ホスト項目ではなく、ネイティブな <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトです。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 VSTO アドイン プロジェクトでは、<xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトの <xref:Microsoft.Office.Tools.Excel.Workbook> ホスト項目を生成できます。 詳細については、「 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
### <a name="to-create-a-new-workbook"></a>新しいブックを作成するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Workbooks> コレクションの <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> メソッドを使用します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]  
  
    > [!NOTE]  
    >  既定のテンプレート以外のテンプレートに基づいてブックを作成できます。その場合は、使用するテンプレートを <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> メソッドにパラメーターとして渡します。  
  
## <a name="see-also"></a>関連項目  
 [実行時の Word 文書と VSTO アドイン内の Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ブックの操作](../vsto/working-with-workbooks.md)   
 [方法: プログラムによってブックを開く](../vsto/how-to-programmatically-open-workbooks.md)   
 [方法: プログラムによってブックを保存](../vsto/how-to-programmatically-save-workbooks.md)   
 [方法: プログラムによってブックを閉じる](../vsto/how-to-programmatically-close-workbooks.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  