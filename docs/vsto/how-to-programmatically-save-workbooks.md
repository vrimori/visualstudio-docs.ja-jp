---
title: "方法: プログラムによってブックを保存する | Microsoft Docs"
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
  - "ブック, 保存"
  - "ブック, 保存 (バックアップ コピーを)"
  - "ブック, 保存 (XML 形式で)"
ms.assetid: 991ccf9b-5213-4094-9030-284ec167bdcc
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# 方法: プログラムによってブックを保存する
  ブックを保存する方法はいくつかあります。  パスを変更しないでブックを保存できます。  以前にブックが保存されていない場合は、パスを指定してブックを保存する必要があります。  明示的なパスがない場合、Microsoft Office Excel は、ファイルが作成されたときに付けられた名前で現在のフォルダーにファイルを保存します。  メモリ内の開いているブックを変更しないで、ブックのコピーを保存することもできます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## パスを変更しないでブックを保存する  
  
#### ドキュメント レベルのカスタマイズに関連付けられているブックを保存するには  
  
1.  ThisWorkbook クラスの <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#4)]  
  
#### VSTO アドインで作業中のブックを保存するには  
  
1.  作業中のブックを保存するには <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> メソッドを呼び出します。  次のコード例を使用するには、Excel 用 VSTO アドイン プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## 新しいパスでブックを保存する  
 指定したブックを、新しい場所にまたは新しい名前を付けて、そしてオプションでファイル形式、パスワード、アクセス モードなどを指定して保存できます。  
  
> [!NOTE]  
>  新しい書式で保存するにはユーザー操作が必要なため、新しいパスでブックを保存する前に、<xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> プロパティを **False** に設定する場合があります。  このプロパティを **False** に設定すると、Excel はすべて既定値を使用します。  
  
#### ドキュメント レベルのカスタマイズに関連付けられているブックを保存するには  
  
1.  `ThisWorkbook` クラスの <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> メソッドを呼び出します。  次のコード例を使用するには、`ThisWorkbook` クラスで実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#5)]  
  
#### VSTO アドインで作業中のブックを保存するには  
  
1.  作業中のブックを新しいパスに保存するには <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> メソッドを呼び出します。  次のコード例を使用するには、Excel 用 VSTO アドイン プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## ブックのコピーを保存する  
 メモリ内の開いているブックを変更しないで、ブックのコピーをファイルに保存することができます。  これは、ブックの場所を変更することがなくバックアップ コピーを作成するときに役立ちます。  
  
#### ドキュメント レベルのカスタマイズに関連付けられているブックを保存するには  
  
1.  `ThisWorkbook` クラスの <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> メソッドを呼び出します。  次のコード例を使用するには、`ThisWorkbook` クラスで実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#6)]  
  
#### VSTO アドインで作業中のブックを保存するには  
  
1.  作業中のブックのコピーを保存するには <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> メソッドを呼び出します。  次のコード例を使用するには、Excel 用 VSTO アドイン プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## 信頼性の高いプログラミング  
 ブックを保存またはコピーするメソッドのいずれかを対話的にキャンセルすると、コード内で実行時エラーが発生します。  たとえば、プロシージャが <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> メソッドを呼び出した際に Excel のプロンプトを無効にしなかった場合、プロンプトが表示されたときにユーザーが **\[キャンセル\]** をクリックすると、Excel で実行時エラーが発生します。  
  
## 参照  
 [ブックの操作](../vsto/working-with-workbooks.md)   
 [Workbook ホスト項目](../vsto/workbook-host-item.md)   
 [方法: プログラムによってブックを閉じる](../vsto/how-to-programmatically-close-workbooks.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  