---
title: "方法: プログラムによってブックからワークシートを削除する | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ブック, 削除 (ワークシートを)"
  - "ワークシート, 削除"
ms.assetid: c5ae99f0-806d-4320-a29c-75ad444fb996
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 方法: プログラムによってブックからワークシートを削除する
  ブック内の任意のワークシートを削除できます。  ワークシートを削除するには、Worksheet ホスト項目を使用するか、ブックの Sheets コレクションを使用してワークシートにアクセスします。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Worksheet ホスト項目の使用  
 デザイン時にドキュメント レベルのカスタマイズでワークシートが追加された場合は、<xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> メソッドを使用して特定のワークシートを削除します。  以下のコードは、Worksheet ホスト項目を直接参照して、ブックからワークシートを削除します。  
  
> [!IMPORTANT]  
>  このコードは、次のプロジェクト テンプレートのいずれかを使用して作成したプロジェクトでのみ実行されます。  
>   
>  -   Excel 2013 ブック  
> -   Excel 2013 テンプレート  
> -   Excel 2010 ブック  
> -   Excel 2010 テンプレート  
>   
>  他の型のプロジェクトでこのタスクを実行する場合は、**Microsoft.Office.Interop.Excel** アセンブリへの参照を追加する必要があります。その後、そのアセンブリのクラスを使用してブックを開き、ワークシートを削除する必要があります。  詳細については、「[方法 : プライマリ相互運用機能アセンブリを利用して Office アプリケーションを使用する](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)」および [Excel 2013 プライマリ相互運用機能アセンブリのリファレンス](http://go.microsoft.com/fwlink/?LinkId=189585)を参照してください。  
  
#### Worksheet ホスト項目を使用してワークシートを削除するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> の `Sheet1` メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#17)]  
  
## Excel ブックの Sheets コレクションの使用  
 次の場合は、Microsoft Office Excel の <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションを使用してワークシートにアクセスします。  
  
-   VSTO アドインでワークシートを削除する場合。  
  
-   削除するワークシートがドキュメント レベルのカスタマイズで実行時に作成された場合。  
  
 以下のコードは、**Sheets** コレクションのインデックス番号でシートを参照して、ブックからワークシートを削除します。  このコードは、新しいワークシートがプログラミングによって作成されたことを前提としています。  
  
> [!IMPORTANT]  
>  他の型のプロジェクトでこのタスクを実行する場合は、**Microsoft.Office.Interop.Excel** アセンブリへの参照を追加する必要があります。その後、そのアセンブリのクラスを使用してブックを開き、ワークシートを削除する必要があります。  詳細については、「[方法 : プライマリ相互運用機能アセンブリを利用して Office アプリケーションを使用する](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)」および [Excel 2013 プライマリ相互運用機能アセンブリのリファレンス](http://go.microsoft.com/fwlink/?LinkId=189585)を参照してください。  
  
#### Excel ブックの Sheets コレクションを使用してワークシートを削除するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションの <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#18)]  
  
## 参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: プログラムによってワークシートを非表示にする](../vsto/how-to-programmatically-hide-worksheets.md)   
 [方法: ブック内のワークシートをプログラムによって移動する](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [方法: プログラムによってワークシートを選択する](../vsto/how-to-programmatically-select-worksheets.md)   
 [方法: プログラムを使用して新しいワークシートをブックに追加する](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  