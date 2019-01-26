---
title: '方法: プログラムによってブックを保護します。'
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5333504ed534373b6bb65902edb2566953de7a59
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863683"
---
# <a name="how-to-programmatically-protect-workbooks"></a>方法: プログラムによってブックを保護します。
  ユーザーできませんを追加またはワークシートを削除してもプログラムによってブックの保護を解除できるように、Microsoft Office Excel ブックを保護することができます。 パスワードを指定して必要に応じてを (そのためユーザーは、のシートを移動することはできません) を保護するには、構造を選択し、保護されているブックのウィンドウを使用するかを指定するかどうかを指定できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ブックの保護では、ユーザーがセルの編集は停止しません。 データを保護するには、ワークシートを保護する必要があります。 詳細については、「[方法 :プログラムによってワークシートを保護](../vsto/how-to-programmatically-protect-worksheets.md)します。  
  
 次のコード例では、ユーザーから取得したパスワードを格納するのに変数を使用します。  
  
## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>ドキュメント レベルのカスタマイズの一部であるブックを保護します。  
  
### <a name="to-protect-a-workbook"></a>ブックを保護する  
  
1.  呼び出す、<xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>ブックのパスワードを指定します。 次のコード例を使用するで実行、`ThisWorkbook`シート クラスではなく、クラス。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]  
  
### <a name="to-unprotect-a-workbook"></a>ブックの保護を解除するには  
  
1.  呼び出す、<xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A>メソッド、必要な場合は、パスワードを渡します。 次のコード例を使用するで実行、`ThisWorkbook`シート クラスではなく、クラス。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]  
  
## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>アプリケーション レベル アドインを使用してブックを保護します。  
  
### <a name="to-protect-a-workbook"></a>ブックを保護する  
  
1.  呼び出す、<xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A>ブックのパスワードを指定します。 このコード例では、作業中のブックを使用します。 この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]  
  
### <a name="to-unprotect-a-workbook"></a>ブックの保護を解除するには  
  
1.  呼び出す、<xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A>パスワードを渡す必要がある場合、アクティブなブックのメソッド。 この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>関連項目  
 [ブックを操作します。](../vsto/working-with-workbooks.md)   
 [方法: プログラムによってワークシートを保護します。](../vsto/how-to-programmatically-protect-worksheets.md)   
 [方法: プログラムによってワークシートを非表示します。](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
