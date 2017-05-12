---
title: "方法: プログラムによってワークシートのセルに文字列を表示する"
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
  - "テキスト [Visual Studio での Office 開発], 追加 (ワークシートに)"
  - "ワークシート, 表示 (ワークシートのセルでテキストを)"
ms.assetid: b19870ad-e132-49fd-994e-0a91710fa4c9
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# 方法: プログラムによってワークシートのセルに文字列を表示する
  プログラムを使用してセルにテキストを表示する方法の例を次に示します。  セルにテキストを表示するには、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールまたはネイティブな Excel 範囲オブジェクトを使用します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## NamedRange コントロールの使用  
 この例では、`message` という名前の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを使用します。  コントロールは、デザイン時にドキュメント レベルのカスタマイズに追加される必要があります。  次のコードは、`ThisWorkbook` クラスではなくシート クラスに配置する必要があります。  
  
#### NamedRange コントロールにテキストを表示するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールの値を **Hello World** に設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#68)]  
  
## ネイティブな Excel 範囲の使用  
 以下のコードは、プログラムで新しい範囲を作成し、値を割り当てます。  
  
#### Excel の範囲にテキストを表示するには  
  
1.  `Sheet1` のセル **A1** の範囲を取得し、値を **Hello World** に設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#69)]  
  
## 参照  
 [チュートリアル : Windows フォームを使用してデータを収集する方法](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Office ソリューションのトラブルシューティング](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  