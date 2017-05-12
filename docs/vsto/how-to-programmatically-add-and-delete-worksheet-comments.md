---
title: "方法: ワークシートのコメントをプログラムによって追加および削除する"
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
  - "範囲、コメント"
  - "ワークシート、コメント"
  - "コメント、ワークシート"
ms.assetid: 3408ce22-a7b7-4e2b-bfc1-dc24d679ee73
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# 方法: ワークシートのコメントをプログラムによって追加および削除する
  Microsoft Office Excel ワークシート内のコメントは、プログラムを使用して追加、削除できます。 コメントは、1 つのセルにのみ追加でき、複数のセル範囲には追加できません。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## ドキュメント レベルのプロジェクト内でのコメントの追加と削除  
 次の例では、`Sheet1` という名前のワークシートに、`dateComment` というシングルセル <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールがあることを想定しています。  
  
#### 名前付き範囲に新しいコメントを追加するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールの <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> メソッドを呼び出し、コメントのテキストを入力します。 このコードは、`Sheet1` クラスに配置する必要があります。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#30)]  
  
#### 名前付き範囲からコメントを削除するには  
  
1.  コメントがその範囲に存在することを確認し、それを削除します。 このコードは、`Sheet1` クラスに配置する必要があります。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#29)]  
  
## VSTO アドイン プロジェクト内でのコメントの追加と削除  
 次の例では、作業中のワークシートに、`dateComment` というシングルセル <xref:Microsoft.Office.Interop.Excel.Range> コントロールがあることを想定しています。  
  
#### Excel 範囲に新しいコメントを追加するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Range> の <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> メソッドを呼び出し、コメントのテキストを入力します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
#### Excel 範囲からコメントを削除するには  
  
1.  コメントがその範囲に存在することを確認し、それを削除します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
## 参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: ワークシートのコメントをプログラムによって表示する](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)  
  
  