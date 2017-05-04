---
title: "方法: プログラムによって新しいブックを作成する | Microsoft Docs"
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
  - "Excel [Visual Studio での Office 開発], 作成 (ブックを)"
  - "ブック, 作成"
ms.assetid: be0196fe-7dc5-4811-b0cd-3c219731a3ff
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 方法: プログラムによって新しいブックを作成する
  プログラムによって作成される新しいブックは、<xref:Microsoft.Office.Tools.Excel.Workbook> ホスト項目ではなく、ネイティブな <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトです。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 VSTO アドイン プロジェクトでは、<xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトの <xref:Microsoft.Office.Tools.Excel.Workbook> ホスト項目を生成できます。  詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
### 新しいブックを作成するには  
  
1.  <xref:Microsoft.Office.Interop.Excel.Workbooks> コレクションの <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> メソッドを使用します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#1)]  
  
    > [!NOTE]  
    >  既定のテンプレート以外のテンプレートに基づいてブックを作成できます。その場合は、使用するテンプレートを <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> メソッドにパラメーターとして渡します。  
  
## 参照  
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ブックの操作](../vsto/working-with-workbooks.md)   
 [方法: プログラムによってブックを開く](../vsto/how-to-programmatically-open-workbooks.md)   
 [方法: プログラムによってブックを保存する](../vsto/how-to-programmatically-save-workbooks.md)   
 [方法: プログラムによってブックを閉じる](../vsto/how-to-programmatically-close-workbooks.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  