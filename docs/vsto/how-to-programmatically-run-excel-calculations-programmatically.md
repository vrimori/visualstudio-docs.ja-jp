---
title: "方法: Excel の計算をプログラムで実行する | Microsoft Docs"
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
  - "計算, 実行 (Excel で)"
  - "Excel [Visual Studio での Office 開発], 実行 (プログラムで計算を)"
  - "範囲, 実行 (計算を)"
  - "ブック, 実行 (計算を)"
ms.assetid: 0bf30d93-8620-43ad-bfb8-f45bf3b5461f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# 方法: Excel の計算をプログラムで実行する
  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールまたはネイティブな Excel 範囲オブジェクトで計算を実行するのと同様のプロセスを使用します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## NamedRange コントロール内での計算の実行  
 セル A1 に <xref:Microsoft.Office.Tools.Excel.NamedRange> を作成してから、そのセルを計算する例を次に示します。  このコードは、`ThisWorkbook` クラスではなくシート クラスに配置する必要があります。  
  
#### NamedRange コントロール内で計算を実行するには  
  
1.  名前付き範囲を作成します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#75](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#75)]  
  
2.  指定された範囲の <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#76](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#76)]  
  
## ネイティブな Excel 範囲での計算の実行  
  
#### ネイティブな Excel 範囲で計算を実行するには  
  
1.  名前付き範囲を作成します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#30)]  
  
2.  指定された範囲の <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#31)]  
  
## 参照  
 [範囲の使用](../vsto/working-with-ranges.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  