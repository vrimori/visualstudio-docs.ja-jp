---
title: "方法: プログラムによって Excel の範囲に色を適用する | Microsoft Docs"
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
  - "色, Excel 範囲"
  - "書式設定 [Visual Studio での Office 開発]"
  - "範囲, 適用 (色を)"
ms.assetid: a9c40229-5308-459a-9216-7e13d82c7cb5
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 方法: プログラムによって Excel の範囲に色を適用する
  セルの範囲にあるテキストに色を適用するには、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールまたはネイティブな Excel 範囲オブジェクトを使用します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## NamedRange コントロールの使用  
 この例は、ドキュメント レベルのカスタマイズ用に作成されています。  
  
#### NamedRange コントロールに色を適用するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールをセル A1 に作成します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#65](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#65)]  
  
2.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロール内のテキストの色を設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#66)]  
  
## ネイティブな Excel 範囲の使用  
  
#### ネイティブな Excel 範囲オブジェクトに色を適用するには  
  
1.  セル A1 に範囲を作成し、テキストの色を設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#67](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#67)]  
  
## 参照  
 [範囲の使用](../vsto/working-with-ranges.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [方法: プログラムによってブック内の範囲にスタイルを適用する](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [方法: プログラムによってコード内でワークシートの範囲を参照する](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  