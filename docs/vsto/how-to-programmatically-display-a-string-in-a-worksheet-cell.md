---
title: "方法: プログラムによってワークシートのセルに文字列を表示 |Microsoft ドキュメント"
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
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
ms.assetid: b19870ad-e132-49fd-994e-0a91710fa4c9
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e297a2f6c1752053557dd7bcea5adab1c2184aa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>方法: プログラムによってワークシートのセルに文字列を表示する
  この例では、プログラムでのセルにテキストを表示する方法を示します。 セルにテキストを表示、いずれかの操作を使用して、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールまたはネイティブな Excel 範囲オブジェクト。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>NamedRange コントロールを使用します。  
 この例では、<xref:Microsoft.Office.Tools.Excel.NamedRange>という名前のコントロール`message`です。 コントロールは、デザイン時にドキュメント レベルのカスタマイズを追加する必要があります。 次のコードではなく、シート クラスに配置する必要があります、`ThisWorkbook`クラスです。  
  
#### <a name="to-display-text-in-a-namedrange-control"></a>NamedRange コントロールにテキストを表示するには  
  
1.  値を設定、<xref:Microsoft.Office.Tools.Excel.NamedRange>に制御を**Hello World**です。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="using-a-native-excel-range"></a>ネイティブ Excel 範囲を使用  
 次のコードでは、新しい範囲をプログラムで作成し、値を代入します。  
  
#### <a name="to-display-text-in-an-excel-range"></a>Excel の範囲にテキストを表示するには  
  
1.  セルでの範囲を取得**A1**で`Sheet1`値を設定および**Hello World**です。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: Windows フォームを使用してデータを収集します。](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Office ソリューションのトラブルシューティング](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  