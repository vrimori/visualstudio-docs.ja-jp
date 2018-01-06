---
title: "方法: プログラムによってワークシートを保護する |Microsoft ドキュメント"
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
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
ms.assetid: 50bde1ff-918a-42ca-ba1b-f22139f8717a
caps.latest.revision: "47"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f653ef0157ed0060066e3aa3ea923794854450d3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-protect-worksheets"></a>方法: プログラムによってワークシートを保護する
  Microsoft Office Excel の保護機能を使用すると、ユーザーやコードがワークシート内のオブジェクトを編集できないようにすることができます。 既定では、保護を有効にすると、すべてのセルがロックされます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ドキュメント レベルのカスタマイズでは、Excel デザイナーを使用してワークシートを保護できます。 プロジェクトの種類に関係なく、実行時にプログラムを使用してワークシートを保護することもできます。  
  
> [!NOTE]  
>  保護されているワークシートの領域に Windows フォーム コントロールを追加することはできません。  
  
## <a name="using-the-designer"></a>デザイナーの使用  
  
#### <a name="to-protect-a-worksheet-in-the-designer"></a>デザイナーでワークシートを保護するには  
  
1.  **変更**のグループ、**レビュー**  タブで、をクリックして**シートの保護**です。  
  
     **シートの保護** ダイアログ ボックスが表示されます。 パスワードを設定し、必要に応じて、セルの書式設定や行の挿入など、ワークシートでユーザーに実行を許可する特定のアクションを指定できます。  
  
 保護されたワークシート内の特定の範囲の編集を、ユーザーに許可することもできます。  
  
#### <a name="to-allow-editing-in-specific-ranges"></a>特定の範囲の編集を許可するには  
  
1.  **変更**のグループ、**レビュー**  タブで、をクリックして**範囲の編集を可能にする**です。  
  
     **範囲の編集を可能にする** ダイアログ ボックスが表示されます。 パスワードを使用してロックを解除できる範囲と、パスワードがなくても範囲を編集できるユーザーを指定できます。  
  
## <a name="using-code-at-run-time"></a>実行時おけるコードの使用  
 次のコードは、(ユーザーから取得したパスワードを格納する変数 getPasswordFromUser を使用して) パスワードを設定し、並べ替えだけを許可します。  
  
#### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズで、コードを使用してワークシートを保護するには  
  
1.  ワークシートの <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> メソッドを呼び出します。 この例では、 `Sheet1`という名前のワークシートを操作していると仮定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]  
  
#### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>VSTO アドインで、コードを使用してワークシートを保護するには  
  
1.  作業中のワークシートの <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]  
  
## <a name="see-also"></a>参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: プログラムによってワークシートの保護を解除](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)   
 [方法: プログラムによってブックを保護します。](../vsto/how-to-programmatically-protect-workbooks.md)   
 [方法: プログラムによってワークシートを非表示](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  