---
title: "方法: プログラムによってワークシートの保護を解除する | Microsoft Docs"
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
  - "ワークシート、保護解除"
  - "ドキュメント [Visual Studio での Office 開発]、ドキュメント保護"
  - "ドキュメント保護、削除 (ワークシートから)"
  - "Unprotect メソッド"
ms.assetid: 034688d2-eda7-4b4a-bcc2-d0999ff879a4
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 方法: プログラムによってワークシートの保護を解除する
  プログラムを使用して、Microsoft Office Excel ワークシートから保護を削除できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 次の例では、変数 `getPasswordFromUser` を使用して、ユーザーから取得したパスワードを格納します。  
  
### ドキュメント レベルのカスタマイズでワークシートの保護を解除するには  
  
1.  ワークシートの <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> メソッドを呼び出して、必要に応じてパスワードを渡します。 この例では、`Sheet1` という名前のワークシートを操作していると仮定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#28)]  
  
### VSTO アドインで、ワークシートの保護を解除するには  
  
1.  アクティブなワークシートの <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> メソッドを呼び出して、必要に応じてパスワードを渡します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#18)]  
  
## 参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: プログラムによってワークシートを保護する](../vsto/how-to-programmatically-protect-worksheets.md)   
 [方法: プログラムによってブックを保護する](../vsto/how-to-programmatically-protect-workbooks.md)   
 [方法: プログラムによってワークシートを非表示にする](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)  
  
  