---
title: "方法: プログラムによってブックからワークシートを削除 |Microsoft ドキュメント"
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
- workbooks, deleting worksheets
- worksheets, deleting
ms.assetid: c5ae99f0-806d-4320-a29c-75ad444fb996
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4fb3251c2e47dab98dd731a56bc0a638587b2812
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>方法: プログラムによってブックからワークシートを削除する
  ブック内の任意のワークシートを削除できます。 ワークシートを削除するには、Worksheet ホスト項目を使用するか、ブックの Sheets コレクションを使用してワークシートにアクセスします。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-the-worksheet-host-item"></a>ワークシートのホスト項目を使用する  
 デザイン時にドキュメント レベルのカスタマイズでワークシートが追加された場合は、<xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> メソッドを使用して特定のワークシートを削除します。 以下のコードは、Worksheet ホスト項目を直接参照して、ブックからワークシートを削除します。  
  
> [!IMPORTANT]  
>  このコードは、次のプロジェクト テンプレートのいずれかを使用して作成したプロジェクトでのみ実行されます。  
>   
>  -   Excel 2013 ブック  
> -   Excel 2013 テンプレート  
> -   Excel 2010 ブック  
> -   Excel 2010 テンプレート  
>   
>  どのその他の種類のプロジェクトでこのタスクを実行する場合への参照を追加する必要があります、 **Microsoft.Office.Interop.Excel**アセンブリ、およびは、ブックを開き、ワークシートを削除するそのアセンブリからクラスを使用する必要があります。 詳細については、次を参照してください。[する方法: ターゲット Office アプリケーション プライマリ相互運用機能アセンブリを利用して](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)と[Excel 2010 プライマリ相互運用機能アセンブリのリファレンス](http://go.microsoft.com/fwlink/?LinkId=189585)です。  
  
#### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Worksheet ホスト項目を使用してワークシートを削除するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> の `Sheet1` メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Excel ブックの Sheets コレクションの使用  
 次の場合は、Microsoft Office Excel の <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションを使用してワークシートにアクセスします。  
  
-   VSTO アドインでワークシートを削除する場合。  
  
-   削除するワークシートがドキュメント レベルのカスタマイズで実行時に作成された場合。  
  
 次のコードでは、ブックからワークシートを削除のインデックス番号でシートを参照することによって、**シート**コレクション。 このコードは、新しいワークシートがプログラミングによって作成されたことを前提としています。  
  
> [!IMPORTANT]  
>  どのその他の種類のプロジェクトでこのタスクを実行する場合への参照を追加する必要があります、 **Microsoft.Office.Interop.Excel**アセンブリ、およびは、ブックを開き、ワークシートを削除するそのアセンブリからクラスを使用する必要があります。 詳細については、次を参照してください。[する方法: ターゲット Office アプリケーション プライマリ相互運用機能アセンブリを利用して](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)と[Excel 2010 プライマリ相互運用機能アセンブリのリファレンス](http://go.microsoft.com/fwlink/?LinkId=189585)です。  
  
#### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Excel ブックの Sheets コレクションを使用してワークシートを削除するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションの <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]  
  
## <a name="see-also"></a>参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: プログラムによってワークシートを非表示](../vsto/how-to-programmatically-hide-worksheets.md)   
 [方法: プログラムによってブック内のワークシートを移動](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [方法: プログラムによってワークシートを選択します。](../vsto/how-to-programmatically-select-worksheets.md)   
 [方法: プログラムによって新しいワークシートをブックに追加](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  