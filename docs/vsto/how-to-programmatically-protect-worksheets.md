---
title: "方法: プログラムによってワークシートを保護する"
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
  - "ドキュメント保護, 追加 (ワークシートに)"
  - "ドキュメント [Visual Studio での Office 開発], ドキュメント保護"
  - "保護, 追加 (ワークシートに)"
  - "ワークシート, 保護"
ms.assetid: 50bde1ff-918a-42ca-ba1b-f22139f8717a
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 方法: プログラムによってワークシートを保護する
  Microsoft Office Excel の保護機能を使用すると、ユーザーやコードがワークシート内のオブジェクトを編集できないようにすることができます。  既定では、保護を有効にすると、すべてのセルがロックされます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ドキュメント レベルのカスタマイズでは、Excel デザイナーを使用してワークシートを保護できます。  プロジェクトの種類に関係なく、実行時にプログラムを使用してワークシートを保護することもできます。  
  
> [!NOTE]  
>  保護されているワークシートの領域に Windows フォーム コントロールを追加することはできません。  
  
## デザイナーの使用  
  
#### デザイナーでワークシートを保護するには  
  
1.  **\[校閲\]** タブの **\[変更\]** で **\[シートの保護\]** をクリックします。  
  
     **\[シートの保護\]** ダイアログ ボックスが表示されます。  パスワードを設定し、必要に応じて、セルの書式設定や行の挿入など、ワークシートでユーザーに実行を許可する特定のアクションを指定できます。  
  
 保護されたワークシート内の特定の範囲の編集を、ユーザーに許可することもできます。  
  
#### 特定の範囲の編集を許可するには  
  
1.  **\[校閲\]** タブの **\[変更\]** で **\[範囲の編集を可能にする\]** をクリックします。  
  
     **\[範囲の編集を可能にする\]** ダイアログ ボックスが表示されます。  パスワードを使用してロックを解除できる範囲と、パスワードがなくても範囲を編集できるユーザーを指定できます。  
  
## 実行時おけるコードの使用  
 次のコードは、\(ユーザーから取得したパスワードを格納する変数 getPasswordFromUser を使用して\) パスワードを設定し、並べ替えだけを許可します。  
  
#### ドキュメント レベルのカスタマイズで、コードを使用してワークシートを保護するには  
  
1.  ワークシートの <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> メソッドを呼び出します。  この例では、`Sheet1` という名前のワークシートを操作していると仮定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#27)]  
  
#### VSTO アドインで、コードを使用してワークシートを保護するには  
  
1.  作業中のワークシートの <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> メソッドを呼び出します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#17)]  
  
## 参照  
 [ワークシートの操作](../vsto/working-with-worksheets.md)   
 [方法: プログラムによってワークシートの保護を解除する](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)   
 [方法: プログラムによってブックを保護する](../vsto/how-to-programmatically-protect-workbooks.md)   
 [方法: プログラムによってワークシートを非表示にする](../vsto/how-to-programmatically-hide-worksheets.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  