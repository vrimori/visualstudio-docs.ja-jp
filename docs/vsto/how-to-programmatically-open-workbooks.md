---
title: "方法: プログラムによってブックを開く |Microsoft ドキュメント"
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
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
ms.assetid: 06c0ac87-a2c6-4cc1-87be-39be0cb81c71
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 541895b941789dd3dbec16e0caad3547f93de904
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-open-workbooks"></a>方法: プログラムによってブックを開く
  <xref:Microsoft.Office.Interop.Excel.Workbooks> Microsoft Office Excel でコレクションにより、すべての開いているブックを使用して、ブックを開きます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-open-an-existing-workbook"></a>既存のブックを開く  
  
1.  使用して、<xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A>のメソッド、<xref:Microsoft.Office.Interop.Excel.Workbooks>コレクション、パスでブックに渡すことです。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコード例で必要な要素は次のとおりです。  
  
-   という名前のブック`YourWorkbook.xls`という名前のディレクトリに存在する必要があります`Test`をドライブ c です。  
  
## <a name="see-also"></a>参照  
 [ブックの操作](../vsto/working-with-workbooks.md)   
 [方法: プログラムによってブックとしてテキスト ファイルを開く](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [方法: プログラムによって新しいブックを作成します。](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [方法: プログラムによってブックを保存](../vsto/how-to-programmatically-save-workbooks.md)   
 [方法: プログラムによってブックを閉じる](../vsto/how-to-programmatically-close-workbooks.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  