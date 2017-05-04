---
title: "方法: プログラムによって Visio 図面を閉じる | Microsoft Docs"
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
  - "図面 [Visual Studio での Office 開発]、閉じる (Visio 図面を)"
  - "Visio [Visual Studio での Office 開発]、閉じる (Visio 図面を)"
ms.assetid: 59c0e215-a4c1-4b39-a491-37534f172705
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 方法: プログラムによって Visio 図面を閉じる
  Microsoft.Office.Interop.Visio.Document.Close メソッドを使用すると、アクティブな Microsoft Office Visio 図面を閉じることができます。  
  
 このメソッドの詳細については、[Microsoft.Office.Interop.Visio.Document.Close](HV10070225) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## 作業中の文書を閉じる  
  
#### 作業中のドキュメントを閉じるには  
  
-   Microsoft.Office.Interop.Visio.Document.Close メソッドを呼び出して、作業中のドキュメントを閉じます。  
  
     次のコード例を使用するには、Visio 用 VSTO アドイン プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## 参照  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [方法: プログラムによって新しい Visio 図面を作成する](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [方法: プログラムによって Visio 図面を開く](../vsto/how-to-programmatically-open-visio-documents.md)   
 [方法: プログラムによって Visio 図面を保存する](../vsto/how-to-programmatically-save-visio-documents.md)   
 [方法: プログラムによって Visio 図面を印刷する](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  