---
title: "方法: プログラムによって文書を印刷する"
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
  - "Word [Visual Studio での Office 開発]、印刷する (ドキュメントを)"
  - "ドキュメント [Visual Studio での Office 開発]、印刷する"
ms.assetid: 99285d98-1bb7-4ccb-83d9-e917b0a9ea42
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# 方法: プログラムによって文書を印刷する
  Microsoft Office Word ドキュメントの全体または一部を既定のプリンターに印刷できます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## ドキュメント レベルのカスタマイズの一部である文書の印刷  
  
#### 文書全体を印刷するには  
  
1.  文書全体を印刷するには、プロジェクトの <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> クラスの `ThisDocument` メソッドを呼び出します。 このコード例を使用するには、`ThisDocument` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#11)]  
  
#### 文書の現在のページを印刷するには  
  
1.  プロジェクトの <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> クラスの `ThisDocument` メソッドを呼び出し、現在のページを一部印刷することを指定します。 このコード例を使用するには、`ThisDocument` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomation#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#12)]  
  
## VSTO アドインを使用した文書の印刷  
  
#### 文書全体を印刷するには  
  
1.  印刷する <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> オブジェクトの <xref:Microsoft.Office.Interop.Word.Document> メソッドを呼び出します。 アクティブ文書を印刷するコード例を次に示します。 この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
#### 文書の現在のページを印刷するには  
  
1.  印刷する <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> オブジェクトの <xref:Microsoft.Office.Interop.Word.Document> メソッドを呼び出し、現在のページを一部印刷することを指定します。 アクティブ文書を印刷するコード例を次に示します。 この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## 参照  
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  