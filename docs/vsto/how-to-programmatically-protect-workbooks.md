---
title: "方法: プログラムによってブックを保護する | Microsoft Docs"
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
  - "ドキュメント保護, 追加 (ブックに)"
  - "ドキュメント保護, 削除 (ブックから)"
  - "ドキュメント [Visual Studio での Office 開発], ドキュメント保護"
  - "ブック, パスワード"
  - "ブック, 保護"
  - "ブック, 保護解除"
ms.assetid: 553c67b9-e2a4-46b6-878c-5b4b4efa4589
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 方法: プログラムによってブックを保護する
  ユーザーがワークシートを追加または削除できないように Microsoft Office Excel ブックを保護できます。また、プログラムでブックの保護を解除できます。  オプションとして、パスワードを指定できます。また、構造を保護する \(ユーザーがシートを移動できないようにする\) かどうか、およびブックのウィンドウを保護するかどうかも指定できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ブックを保護しても、ユーザーはセルを編集できます。  データを保護するには、ワークシートを保護する必要があります。  詳細については、「[方法: プログラムによってワークシートを保護する](../vsto/how-to-programmatically-protect-worksheets.md)」を参照してください。  
  
 次のコード例では、ユーザーから受け取ったパスワードを格納する変数を使用しています。  
  
## ドキュメント レベルのカスタマイズの一部であるブックの保護  
  
#### ブックを保護するには  
  
1.  ブックの <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> メソッドを呼び出し、パスワードを指定します。  次のコード例を使用するには、シート クラスではなく、`ThisWorkbook` クラスで実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#10)]  
  
#### ブックの保護を解除するには  
  
1.  <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> メソッドを呼び出して、必要に応じてパスワードを渡します。  次のコード例を使用するには、シート クラスではなく、`ThisWorkbook` クラスで実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#11)]  
  
## アプリケーション レベルのアドインを使用したブックの保護  
  
#### ブックを保護するには  
  
1.  ブックの <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> メソッドを呼び出し、パスワードを指定します。  このコード例ではアクティブなブックを使用します。  この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
#### ブックの保護を解除するには  
  
1.  アクティブなブックの <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> メソッドを呼び出して、必要に応じてパスワードを渡します。  この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## 参照  
 [ブックの操作](../vsto/working-with-workbooks.md)   
 [方法: プログラムによってワークシートを保護する](../vsto/how-to-programmatically-protect-worksheets.md)   
 [方法: プログラムによってワークシートを非表示にする](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  