---
title: "方法: プログラムを使用してワークシート内のデータを並べ替える | Microsoft Docs"
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
  - "データ [Visual Studio での Office 開発], 並べ替え (ワークシートで)"
  - "データの並べ替え, ワークシート"
  - "並べ替え (データの), ワークシートで"
  - "ワークシート, 並べ替え (データの)"
ms.assetid: 2fbc6e63-02ea-4624-8d6f-bed60e06c61e
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# 方法: プログラムを使用してワークシート内のデータを並べ替える
  実行時にワークシートの範囲およびリストに含まれているデータを並べ替えることができます。  次のコードは、複数の列で構成される `Fruits` という名前の範囲を、最初の列のデータを基に並べ替え、次に 2 番目の列のデータを基に並べ替えます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## ドキュメント レベルのカスタマイズにおけるデータの並べ替え  
  
#### NamedRange コントロール内のデータを並べ替えるには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールの <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> メソッドを呼び出します。  次のコード例では、ワークシートに `Fruits` という名前の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールが必要です。  このコードは、`ThisWorkbook` クラスではなく、シート クラスに配置する必要があります。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#78)]  
  
 次のコードを Sheet1.vb または Sheet1.cs に配置して、<xref:Microsoft.Office.Tools.Excel.ListObject> コントロール内のデータを並べ替えます。  このコードでは、`Sheet1` という名前のワークシートに、`fruitList` という名前の <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールがあることを前提としています。  
  
#### ListObject コントロール内のデータを並べ替えるには  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject> ホスト コントロールの <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> プロパティの <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#79)]  
  
## VSTO アドイン内のデータの並べ替え  
  
#### ネイティブな範囲でデータを並べ替えるには  
  
1.  ネイティブな Excel <xref:Microsoft.Office.Interop.Excel.Range> コントロールの <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> メソッドを呼び出します。  次のコード例では、ワークシートに `Fruits` という名前のネイティブな Excel コントロールが必要です。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
#### ListObject コントロール内のデータを並べ替えるには  
  
1.  ネイティブな Excel <xref:Microsoft.Office.Interop.Excel.ListObject> コントロールの <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> プロパティの <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> メソッドを呼び出します。  次の例は、作業中のワークシートに `fruitList` という名前のネイティブな Excel <xref:Microsoft.Office.Interop.Excel.ListObject> コントロールがあることを前提としています。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## 参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: 増分するデータを範囲内にプログラムによって自動的に入力する](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [方法: プログラムによってコード内でワークシートの範囲を参照する](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [方法: プログラムによってブック内の範囲にスタイルを適用する](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  