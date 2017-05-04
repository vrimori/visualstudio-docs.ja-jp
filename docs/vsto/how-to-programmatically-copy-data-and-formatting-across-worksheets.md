---
title: "方法: プログラムによって複数のワークシートにデータと書式設定をコピーする | Microsoft Docs"
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
  - "コピー (データを), Visual Studio での Office 開発"
  - "データ [Visual Studio での Office 開発], コピー (ワークシート間で)"
  - "書式設定 [Visual Studio での Office 開発]"
  - "ワークシート, コピー (データを)"
ms.assetid: eed7dbaf-bdb5-4330-ba2e-5f3d50817eca
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 方法: プログラムによって複数のワークシートにデータと書式設定をコピーする
  <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> メソッドを使用すると、1 つのシートの範囲内のデータをブック内の他のすべてのシートにコピーできます。  このとき、範囲とコピー対象 \(データか書式設定、または両方\) を指定します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 使用例  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#44)]  
  
## コードのコンパイル  
 この例では、ワークシート内に `rangeData` という名前の範囲が必要です。  
  
## 参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: プログラムを使用して新しいワークシートをブックに追加する](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [方法: 選択されたセルを含むワークシートの行の書式をプログラムによって変更する](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  