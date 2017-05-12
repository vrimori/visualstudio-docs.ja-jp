---
title: "方法: プログラムによって Visio 図面を印刷する"
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
  - "Visio [Visual Studio での Office 開発]、印刷する (Visio 図面を)"
  - "図面 [Visual Studio での Office 開発]、印刷する (Visio 図面を)"
ms.assetid: 606a2678-5eb8-40b2-a50a-305cecb1b3d4
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 方法: プログラムによって Visio 図面を印刷する
  Microsoft Office Visio 図面の全体または特定のページだけを印刷することができます。  
  
 印刷メソッドの詳細については、[Microsoft.Office.Interop.Visio.Document.Print](HV10070345) メソッドと [Microsoft.Office.Interop.Visio.Page.Print](HV10070404) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## Visio 図面を印刷する  
  
#### 図面全体を印刷するには  
  
-   印刷する Microsoft.Office.Interop.Visio.Document.Print オブジェクトの Microsoft.Office.Interop.Visio.Document メソッドを呼び出します。  
  
     アクティブ文書を印刷するコード例を次に示します。 この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#8)]  
  
## Visio 図面の特定のページを印刷する  
  
#### 特定のページの図面を印刷するには  
  
-   印刷する Microsoft.Office.Interop.Visio.Pages.Print オブジェクトの Microsoft.Office.Interop.Visio.Pages メソッドを呼び出します。  
  
     アクティブ文書の最初のページを印刷するコード例を次に示します。 この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#9)]  
  
## 参照  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [方法: プログラムによって新しい Visio 図面を作成する](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [方法: プログラムによって Visio 図面を開く](../vsto/how-to-programmatically-open-visio-documents.md)   
 [方法: プログラムによって Visio 図面を閉じる](../vsto/how-to-programmatically-close-visio-documents.md)   
 [方法: プログラムによって Visio 図面を保存する](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  