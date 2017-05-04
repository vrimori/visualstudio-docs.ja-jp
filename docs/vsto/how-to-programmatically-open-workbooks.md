---
title: "方法: プログラムによってブックを開く | Microsoft Docs"
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
  - "Excel [Visual Studio での Office 開発], 開く (ブックを)"
  - "ブック, 開く"
ms.assetid: 06c0ac87-a2c6-4cc1-87be-39be0cb81c71
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# 方法: プログラムによってブックを開く
  Microsoft Office Excel の <xref:Microsoft.Office.Interop.Excel.Workbooks> コレクションを使用すると、開いているすべてのブックを操作し、ブックを開くことができます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 既存のブックを開くには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Workbooks> コレクションの <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> メソッドを使用して、ブックのパスを指定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#2)]  
  
## コードのコンパイル  
 このコード例に必要な条件は次のとおりです。  
  
-   `YourWorkbook.xls` という名前のブックが、ドライブ C の `Test` ディレクトリに存在する。  
  
## 参照  
 [ブックの操作](../vsto/working-with-workbooks.md)   
 [方法: プログラムによってテキスト ファイルをブックとして開く](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [方法: プログラムによって新しいブックを作成する](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [方法: プログラムによってブックを保存する](../vsto/how-to-programmatically-save-workbooks.md)   
 [方法: プログラムによってブックを閉じる](../vsto/how-to-programmatically-close-workbooks.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  