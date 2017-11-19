---
title: "方法: プログラムによってブックを保護する |Microsoft ドキュメント"
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
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
ms.assetid: 553c67b9-e2a4-46b6-878c-5b4b4efa4589
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7dcbedb2c30758c762af0c301c239dd03fe4b10f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-protect-workbooks"></a>方法: プログラムによってブックを保護する
  Microsoft Office Excel ブックを保護するには、ユーザーことはできませんを追加またはワークシートを削除してもプログラムによってブックの保護を解除できるようにします。 必要に応じて、パスワードを指定して、構造を (したがって、ユーザーは、シートを移動することはできません) を保護、および、保護されているブックのウィンドウを使用するかを指定するかどうかを示すことができます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ブックの保護では、ユーザーがセルの編集は停止しません。 データを保護するのには、ワークシートを保護する必要があります。 詳細については、次を参照してください。[する方法: プログラムによってワークシートを保護する](../vsto/how-to-programmatically-protect-worksheets.md)です。  
  
 次のコード例では、ユーザーから取得されるパスワードを格納するのに変数を使用します。  
  
## <a name="protecting-a-workbook-that-is-part-of-a-document-level-customization"></a>ドキュメント レベルのカスタマイズの一部であるブックの保護  
  
#### <a name="to-protect-a-workbook"></a>ブックを保護する  
  
1.  呼び出す、<xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>ブックのパスワードを指定します。 使用するには次のコード例実行、`ThisWorkbook`シート クラスではなく、クラスです。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]  
  
#### <a name="to-unprotect-a-workbook"></a>ブックの保護を解除するには  
  
1.  呼び出す、<xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A>メソッド、必要な場合は、パスワードを渡すことです。 使用するには次のコード例実行、`ThisWorkbook`シート クラスではなく、クラスです。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]  
  
## <a name="protecting-a-workbook-by-using-an-application-level-add-in"></a>アプリケーション レベルのアドインを使用してブックの保護  
  
#### <a name="to-protect-a-workbook"></a>ブックを保護する  
  
1.  呼び出す、<xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A>ブックのパスワードを指定します。 このコード例では、作業中のブックを使用します。 この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]  
  
#### <a name="to-unprotect-a-workbook"></a>ブックの保護を解除するには  
  
1.  呼び出す、<xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A>パスワードを渡す必要がある場合、作業中のブックのメソッドです。 この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>関連項目  
 [ブックの操作](../vsto/working-with-workbooks.md)   
 [方法: プログラムによってワークシートを保護します。](../vsto/how-to-programmatically-protect-worksheets.md)   
 [方法: プログラムによってワークシートを非表示](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  