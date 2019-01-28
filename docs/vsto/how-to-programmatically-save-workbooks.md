---
title: '方法: プログラムによってブックを保存します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bcc0869b8d255ba91e1a1fd017c93cdb24346b27
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874550"
---
# <a name="how-to-programmatically-save-workbooks"></a>方法: プログラムによってブックを保存します。
  ブックを保存する方法はいくつかあります。 パスを変更しないでブックを保存できます。 以前にブックが保存されていない場合は、パスを指定してブックを保存する必要があります。 明示的なパスがない場合、Microsoft Office Excel は、ファイルが作成されたときに付けられた名前で現在のフォルダーにファイルを保存します。 メモリ内の開いているブックを変更しないで、ブックのコピーを保存することもできます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="save-a-workbook-without-changing-the-path"></a>パスを変更しないでブックを保存します。  
  
### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>ドキュメント レベルのカスタマイズに関連付けられているブックを保存するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> クラスの `ThisWorkbook` メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]  
  
### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>VSTO アドインで作業中のブックを保存するには  
  
1.  作業中のブックを保存するには <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> メソッドを呼び出します。 次のコード例を使用するには、Excel 用 VSTO アドイン プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="save-a-workbook-with-a-new-path"></a>新しいパスでブックを保存します。  
 指定したブックを、新しい場所にまたは新しい名前を付けて、そしてオプションでファイル形式、パスワード、アクセス モードなどを指定して保存できます。  
  
> [!NOTE]  
>  設定することがあります、<xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A>プロパティを**False**前に、いくつかの形式で保存するために、新しいパスでブックを保存操作が必要です。 このプロパティを設定**False**すべて既定値を使用するように Excel。  
  
### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>ドキュメント レベルのカスタマイズに関連付けられているブックを保存するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> クラスの `ThisWorkbook` メソッドを呼び出します。 次のコード例を使用するには、`ThisWorkbook` クラスで実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]  
  
### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>VSTO アドインで作業中のブックを保存するには  
  
1.  作業中のブックを新しいパスに保存するには <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> メソッドを呼び出します。 次のコード例を使用するには、Excel 用 VSTO アドイン プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="save-a-copy-of-the-workbook"></a>ブックのコピーを保存します。  
 メモリ内の開いているブックを変更しないで、ブックのコピーをファイルに保存することができます。 これは、ブックの場所を変更することがなくバックアップ コピーを作成するときに役立ちます。  
  
### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>ドキュメント レベルのカスタマイズに関連付けられているブックを保存するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> クラスの `ThisWorkbook` メソッドを呼び出します。 次のコード例を使用するには、`ThisWorkbook` クラスで実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]  
  
### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>VSTO アドインで作業中のブックを保存するには  
  
1.  作業中のブックのコピーを保存するには <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> メソッドを呼び出します。 次のコード例を使用するには、Excel 用 VSTO アドイン プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ブックを保存またはコピーするメソッドのいずれかを対話的にキャンセルすると、コード内で実行時エラーが発生します。 プロシージャを呼び出す場合など、<xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A>メソッドが無効にしなかったが、Excel からメッセージが表示されますと、ユーザーがクリックした**キャンセル**を求められたら、実行時エラーが発生します。  
  
## <a name="see-also"></a>関連項目  
 [ブックを操作します。](../vsto/working-with-workbooks.md)   
 [Workbook ホスト項目](../vsto/workbook-host-item.md)   
 [方法: プログラムによってブックを閉じる](../vsto/how-to-programmatically-close-workbooks.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
