---
title: "方法: 最近使用したブック ファイルをプログラムによって一覧表示する | Microsoft Docs"
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
  - "Excel [Visual Studio での Office 開発], 最近使用したファイルの一覧表示"
  - "最近使ったファイルの一覧, Excel"
  - "RecentFiles プロパティ"
  - "ブック, 一覧表示 (最近使ったブックを)"
ms.assetid: 210a3753-4845-4875-b34a-a30d3a1299b3
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 方法: 最近使用したブック ファイルをプログラムによって一覧表示する
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> プロパティは、Microsoft Office Excel の最近使用したファイルの一覧に表示されるすべてのファイルの名前が含まれるコレクションを返します。  一覧の長さは、ユーザーが保持するように指定したファイルの数によって変わります。  結果は範囲に表示できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 最近使用したブックを範囲オブジェクトに一覧表示するには  
  
1.  最近使用したファイルの一覧をループし、<xref:Microsoft.Office.Interop.Excel.Range> オブジェクトを基準とするセルに名前を表示します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#9)]  
  
## 参照  
 [ブックの操作](../vsto/working-with-workbooks.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  