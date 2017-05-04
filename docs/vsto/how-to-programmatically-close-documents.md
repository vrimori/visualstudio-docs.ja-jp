---
title: "方法: プログラムによって文書を閉じる | Microsoft Docs"
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
  - "ドキュメント [Visual Studio での Office 開発]、閉じる"
  - "Word [Visual Studio での Office 開発]、閉じる (ドキュメントを)"
ms.assetid: d5bee1dc-63d1-4307-828f-b7b077e20fb9
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# 方法: プログラムによって文書を閉じる
  作業中の文書を閉じたり、文書を指定して閉じたりすることができます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 作業中の文書を閉じる  
 作業中の文書を閉じる手順には、ドキュメント レベルのカスタマイズでの手順と VSTO アドインでの手順の 2 つがあります。  
  
#### ドキュメント レベルのカスタマイズで作業中の文書を閉じるには  
  
1.  プロジェクトの `ThisDocument` クラスの <xref:Microsoft.Office.Tools.Word.Document.Close%2A> メソッドを呼び出して、カスタマイズに関連付けられた文書を閉じます。 次のコード例を使用するには、`ThisDocument` クラスからコードを実行します。  
  
    > [!NOTE]  
    >  この例では、変更内容を保存したりユーザーにメッセージを表示したりせずに文書を閉じるために、*SaveChanges* パラメーターに <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 値を渡します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomation#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#3)]  
  
#### VSTO アドインで作業中の文書を閉じるには  
  
1.  <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> プロパティの <xref:Microsoft.Office.Interop.Word._Document.Close%2A> メソッドを呼び出して、作業中の文書を閉じます。 次のコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
    > [!NOTE]  
    >  この例では、変更内容を保存したりユーザーにメッセージを表示したりせずに文書を閉じるために、*SaveChanges* パラメーターに <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 値を渡します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## 名前を指定して文書を閉じる  
 名前を指定して文書を閉じる方法は、VSTO アドインとドキュメント レベルのカスタマイズで同じです。  
  
#### 名前を指定して文書を閉じるには  
  
1.  <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> コレクションへの引数として文書名を指定して、<xref:Microsoft.Office.Interop.Word._Document.Close%2A> メソッドを呼び出します。 次のコード例は、Word で「**NewDocument**」という名前の文書が開いていることを前提としています。  
  
    > [!NOTE]  
    >  この例では、変更内容を保存したりユーザーにメッセージを表示したりせずに文書を閉じるために、*SaveChanges* パラメーターに <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> 値を渡します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreWordAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#4)]  
  
## 参照  
 [方法: プログラムによって既存文書を開く](../vsto/how-to-programmatically-open-existing-documents.md)   
 [方法: プログラムによって文書を保存する](../vsto/how-to-programmatically-save-documents.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  