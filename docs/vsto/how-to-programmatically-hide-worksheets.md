---
title: "方法: プログラムによってワークシートを非表示にする | Microsoft Docs"
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
  - "非表示のワークシート"
  - "ワークシート、非表示"
ms.assetid: 3208f633-137f-47f9-9c9c-2cf8e3c72096
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 方法: プログラムによってワークシートを非表示にする
  ブック内の任意のワークシートの表示と非表示を切り替えることができます。 ワークシートを非表示にするには、Worksheet ホスト項目を使用するか、ブックの Sheets コレクションを使用してワークシートにアクセスします。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## ワークシートのホスト項目を使用する  
 デザイン時にドキュメント レベルのカスタマイズでワークシートが追加された場合は、<xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> プロパティを使用して特定のワークシートを非表示にします。  
  
#### Worksheet ホスト項目を使用してワークシートを非表示にするには  
  
1.  `Sheet1` ホスト項目の <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> プロパティを列挙値 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> に設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#25)]  
  
## Excel ブックの Sheets コレクションの使用  
 次の場合は、Microsoft Office Excel の <xref:Microsoft.Office.Interop.Excel.Sheets> コレクションを使用してワークシートにアクセスします。  
  
-   VSTO アドインでワークシートを非表示にする場合。  
  
-   非表示にするワークシートがドキュメント レベルのカスタマイズで実行時に作成された場合。  
  
#### Excel ブックの Sheets コレクションを使用してワークシートを非表示にするには  
  
1.  ワークシートの <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> プロパティを列挙値 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> に設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#26)]  
  
## 参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: プログラムによってブックからワークシートを削除する](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [方法: ブック内のワークシートをプログラムによって移動する](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [方法: プログラムによってワークシートを保護する](../vsto/how-to-programmatically-protect-worksheets.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)  
  
  