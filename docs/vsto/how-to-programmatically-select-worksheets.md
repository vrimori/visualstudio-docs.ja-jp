---
title: "方法: プログラムによってワークシートを選択する"
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
  - "Excel プロジェクト, 選択 (ワークシートを)"
  - "ワークシート, 選択"
ms.assetid: 9e7cdb11-e825-4c9f-abcd-d46fd20dc5e0
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 方法: プログラムによってワークシートを選択する
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> メソッドは指定されたオブジェクトを選択します。これにより、ユーザーの選択が新しいオブジェクトに移動します。  ユーザーの選択を変更せずにフォーカスをオブジェクトに移動する場合は、<xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> メソッドを使用します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 VSTO アドインで既存のワークシートを選択する場合、または、ドキュメント レベルのカスタマイズでワークシートが実行時に作成された場合は、Excel ブックの Excel  <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションを使用してこれにアクセスする必要があります。それ以外の場合は、<xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目に直接アクセスできます。  
  
## ワークシートのホスト項目を使用する  
 ドキュメント レベルのカスタマイズでは、次のコードを **Sheet1.vb** または **Sheet1.cs** に追加します。  
  
#### ホスト項目を使用してブック内の最初のワークシートを選択するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> の `Sheet1` メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#19)]  
  
## Excel ブックの Sheets コレクションの使用  
 Excel の <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションを使用して、ワークシートにアクセスします。  
  
#### Excel ブックの Sheets コレクションを使用して、ブック内の最初のワークシートを選択するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションの <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> メソッドを呼び出して、作業中のブックの最初のワークシートを選択します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#20)]  
  
## 参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: プログラムによってワークシートを印刷する](../vsto/how-to-programmatically-print-worksheets.md)   
 [方法: プログラムによってブックからワークシートを削除する](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [方法: プログラムによってワークシートを非表示にする](../vsto/how-to-programmatically-hide-worksheets.md)   
 [方法: プログラムによってワークシートを保護する](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  