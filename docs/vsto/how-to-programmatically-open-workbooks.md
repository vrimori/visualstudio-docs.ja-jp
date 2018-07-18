---
title: '方法: プログラムによってブックを開く'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cd8f6786bd2f7b54ce6b50f2493ebd5d45bba51e
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257359"
---
# <a name="how-to-programmatically-open-workbooks"></a>方法: プログラムによってブックを開く
  <xref:Microsoft.Office.Interop.Excel.Workbooks> Microsoft Office Excel でのコレクションでは、すべての開いているブックを操作し、ブックを開くには可能です。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-open-an-existing-workbook"></a>既存のブックを開く  
  
1.  使用して、<xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A>のメソッド、<xref:Microsoft.Office.Interop.Excel.Workbooks>パスでブックに渡すコレクション。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compile-the-code"></a>コードをコンパイルします  
 このコード例で必要な要素は次のとおりです。  
  
-   という名前のブック`YourWorkbook.xls`という名前のディレクトリに存在する必要があります`Test`失われます。  
  
## <a name="see-also"></a>関連項目  
 [ブックを操作します。](../vsto/working-with-workbooks.md)   
 [方法: プログラムによってブックとしてテキスト ファイルを開く](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [方法: プログラムによって新しいブックを作成](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [方法: プログラムによってブックを保存](../vsto/how-to-programmatically-save-workbooks.md)   
 [方法: プログラムによってブックを閉じる](../vsto/how-to-programmatically-close-workbooks.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  