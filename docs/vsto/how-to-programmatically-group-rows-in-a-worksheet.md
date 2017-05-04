---
title: "方法: プログラムによってワークシート内の行をグループ化する | Microsoft Docs"
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
  - "列 [Visual Studio での Office 開発], グループ化解除"
  - "グループ"
  - "グループ [Visual Studio での Office 開発], クリア (ワークシートを)"
  - "グループ, 作成 (ワークシートで)"
  - "範囲, 作成 (グループを)"
  - "行 [Visual Studio での Office 開発], グループ化解除"
  - "ワークシート, クリア (グループを)"
  - "ワークシート, 作成 (グループを)"
  - "ワークシート, グループ化解除 (行と列の)"
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 方法: プログラムによってワークシート内の行をグループ化する
  1 つ以上の行をグループ化できます。  ワークシートにグループを作成するには、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールまたはネイティブな Excel 範囲オブジェクトを使用します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## NamedRange コントロールの使用  
 デザイン時にドキュメント レベルのプロジェクトに <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを追加する場合、そのコントロールを使用してプログラムでグループを作成できます。  次の例では、同じワークシートに 3 つの <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロール \(`data2001`、`data2002`、および `dataAll`\) があることを前提としています。  名前付き範囲はそれぞれ、ワークシートの行全体を参照します。  
  
#### NamedRange コントロールのグループをワークシートに作成するには  
  
1.  それぞれの範囲の <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> メソッドを呼び出して、3 つの名前付き範囲をグループ化します。  このコードは、`ThisWorkbook` クラスではなくシート クラスに配置する必要があります。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  行のグループ化を解除するには、<xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> メソッドを呼び出します。  
  
## ネイティブな Excel 範囲の使用  
 このコードでは、ワークシートに `data2001`、`data2002`、および `dataAll` という 3 つの Excel 範囲があることを前提としています。  
  
#### ワークシート内に Excel 範囲のグループを作成するには  
  
1.  それぞれの範囲の <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> メソッドを呼び出して、3 つの名前付き範囲をグループ化します。  次の例では、同じワークシートに `data2001`、`data2002`、および `dataAll` という名前の 3 つの <xref:Microsoft.Office.Interop.Excel.Range> コントロールがあることを前提としています。  名前付き範囲はそれぞれ、ワークシートの行全体を参照します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  行のグループ化を解除するには、<xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> メソッドを呼び出します。  
  
## 参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [方法 : ワークシートに NamedRange コントロールを追加する](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  