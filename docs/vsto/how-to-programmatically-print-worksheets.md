---
title: "方法: プログラムによってワークシートを印刷する | Microsoft Docs"
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
  - "印刷プレビュー, ワークシート"
  - "印刷 [Visual Studio での Office 開発], ワークシート"
  - "ワークシート, 印刷"
ms.assetid: 312bfcd7-0a74-421c-b42e-df71a06b7bdf
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 方法: プログラムによってワークシートを印刷する
  ブック内のワークシートはすべて印刷できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## ドキュメント レベルのカスタマイズでのワークシートの印刷  
  
#### ワークシートを印刷するには  
  
1.  `Sheet1` の <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> メソッドを呼び出します。印刷部数は 2 部で、印刷前に文書をプレビューします。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomation#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#22)]  
  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> メソッドを使用すると、指定したオブジェクトを **\[印刷プレビュー\]** ウィンドウに表示できます。  次のコードでは、`Sheet1` という名前の <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目があることを前提としています。  
  
#### 印刷する前にページをプレビューするには  
  
1.  ワークシートの <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#23)]  
  
## VSTO アドインでのワークシートの印刷  
  
#### ワークシートを印刷するには  
  
1.  作業中のワークシートの <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> メソッドを呼び出します。印刷部数は 2 部で、印刷前に文書をプレビューします。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#14)]  
  
 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> メソッドを使用すると、指定したオブジェクトを **\[印刷プレビュー\]** ウィンドウに表示できます。  
  
#### 印刷する前にページをプレビューするには  
  
1.  作業中のワークシートの <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#15)]  
  
## 参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: プログラムを使用してワークシートでスペル チェックを行う](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  