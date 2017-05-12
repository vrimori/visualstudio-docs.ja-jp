---
title: "方法: プログラムによって Excel の範囲内のデータの値を格納および取得する"
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
  - "日付値"
  - "日付値, 格納 (Excel 範囲で)"
  - "日付, 取得 (Excel 範囲から)"
  - "日付, 格納 (Excel 範囲で)"
  - "Excel [Visual Studio での Office 開発], 取得 (日付値を範囲から)"
  - "Excel [Visual Studio での Office 開発], 格納 (日付値を範囲で)"
  - "範囲, 取得 (データ値を)"
  - "範囲, 格納 (日付値を)"
ms.assetid: e1cdd262-0356-4499-8bc5-e730f74235a2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 方法: プログラムによって Excel の範囲内のデータの値を格納および取得する
  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールまたはネイティブな Excel 範囲オブジェクトに対して値の格納や取得を行うことができます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Visual Studio の Office 開発ツールを使用して 1900 年 1 月 1 日以降の日付の値を範囲に格納した場合、その値は OLE オートメーション \(OA\) 形式で格納されます。  OLE オートメーション \(OA\) の日付の値を取得するには、<xref:System.DateTime.FromOADate%2A> メソッドを使用する必要があります。  1900 年 1 月 1 日より前の日付は文字列として格納されます。  
  
> [!NOTE]  
>  1900 年の最初の 2 か月については、Excel の日付と OLE オートメーションの日付は異なります。  **\[1904 年から計算する\]** オプションがオンである場合も、この違いはあります。  以下のコード例は、こうした違いには対応していません。  
  
## NamedRange コントロールの使用  
  
-   この例は、ドキュメント レベルのカスタマイズ用に作成されています。  次のコードは、`ThisWorkbook` クラスではなくシート クラスに配置する必要があります。  
  
#### 名前付き範囲に日付の値を格納するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールをセル **A1** に作成します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#50)]  
  
2.  `NamedRange1` の値として今日の日付を設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#51)]  
  
#### 名前付き範囲から日付の値を取得するには  
  
1.  `NamedRange1` から日付の値を取得します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#52)]  
  
## ネイティブな Excel 範囲の使用  
  
#### ネイティブな Excel 範囲オブジェクトに日付の値を格納するには  
  
1.  セル **A1** を表す <xref:Microsoft.Office.Interop.Excel.Range> を作成します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
2.  `rng` の値として今日の日付を設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
#### ネイティブな Excel 範囲オブジェクトから日付の値を取得するには  
  
1.  `rng` から日付の値を取得します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
## 参照  
 [範囲の使用](../vsto/working-with-ranges.md)   
 [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [方法: プログラムによってコード内でワークシートの範囲を参照する](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [方法 : ワークシートに NamedRange コントロールを追加する](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  