---
title: "方法: 増分するデータを範囲内にプログラムによって自動的に入力する | Microsoft Docs"
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
  - "Autofill メソッド [Excel]"
  - "入力 (範囲内に自動的に)"
  - "範囲, 自動入力"
  - "ブック, 入力範囲"
ms.assetid: 27639d55-8ab5-483c-8907-2ea50dfd2188
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# 方法: 増分するデータを範囲内にプログラムによって自動的に入力する
  <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトの <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> メソッドを使用すると、ワークシート内の範囲に、値を自動的に入力できます。  通常 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> メソッドは、インクリメント方式で増加または減少する値を範囲に入力するために使用します。  次に示す <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> 列挙体の定数を与えて動作を指定することもできます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> を使用する場合は、2 つの範囲を指定する必要があります。  
  
-   <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> メソッドの呼び出し元の範囲。これは、入力を開始する場所を指定し、初期値を格納します。  
  
-   データの入力先の範囲。これは、パラメーターとして <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> メソッドに渡されます。  データの入力先の範囲には、初期値を格納する範囲も含まれます。  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Interop.Excel.Range> の代わりに、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを渡すことはできません。  詳細については、「[ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)」を参照してください。  
  
## 使用例  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#49)]  
  
## コードのコンパイル  
 入力対象範囲の最初のセルには、初期値を入力する必要があります。  
  
 例では、3 つの範囲に入力する必要があります。  
  
-   列 B には、平日 5 日分の曜日が入力されます。  初期値として、セル B1 に「**Monday**」と入力します。  
  
-   列 C には、5 か月分の月が入力されます。  初期値として、セル C1 に「**January**」と入力します。  
  
-   列 D には、行単位で 2 つずつ増分する一連の数字が入力されます。  初期値として、セル D1 に「**4**」と入力し、セル D2 に「**6**」と入力します。  
  
## 参照  
 [範囲の使用](../vsto/working-with-ranges.md)   
 [方法: プログラムによってコード内でワークシートの範囲を参照する](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [方法: プログラムによってブック内の範囲にスタイルを適用する](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [方法: Excel の計算をプログラムで実行する](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  