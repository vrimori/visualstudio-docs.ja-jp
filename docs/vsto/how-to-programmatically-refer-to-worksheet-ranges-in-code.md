---
title: "方法: プログラムによってコード内でワークシートの範囲を参照する"
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
  - "Excel [Visual Studio での Office 開発], 参照 (ワークシートの範囲を)"
  - "範囲, 参照"
  - "参照 (ワークシートの範囲を)"
  - "ワークシート, 参照 (範囲を)"
ms.assetid: 113633b8-426a-4d02-b6b8-d459d1f110ea
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 方法: プログラムによってコード内でワークシートの範囲を参照する
  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールまたはネイティブな Excel 範囲オブジェクトの内容を参照するのと同様のプロセスを使用します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## NamedRange コントロールの使用  
 次のコード例は、<xref:Microsoft.Office.Tools.Excel.NamedRange> をワークシートに追加し、その範囲内のセルにテキストを追加します。  
  
#### NamedRange コントロールを参照するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールの <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> プロパティに文字列を代入します。  このコードは、`ThisWorkbook` クラスではなくシート クラスに配置する必要があります。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#46)]  
  
## ネイティブな Excel 範囲の使用  
 次のコード例は、ネイティブな Excel 範囲をワークシートに追加し、その範囲内のセルにテキストを追加します。  
  
#### ネイティブな範囲オブジェクトを参照するには  
  
1.  文字列を範囲の <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> プロパティに割り当てます。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#47)]  
  
## 参照  
 [範囲の使用](../vsto/working-with-ranges.md)   
 [方法: プログラムを使用してワークシートでスペル チェックを行う](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [方法: プログラムによってブック内の範囲にスタイルを適用する](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [方法: 増分するデータを範囲内にプログラムによって自動的に入力する](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [方法: プログラムによってワークシートの範囲内のテキストを検索する](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  