---
title: "方法: プログラムによって Visio 図面を開く | Microsoft Docs"
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
  - "ドキュメント [Visual Studio での Office 開発]、開く (Visio 図面を)"
  - "Visio [Visual Studio での Office 開発]、開く (Visio 図面を)"
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 方法: プログラムによって Visio 図面を開く
  既存の Microsoft Office Visio 図面を開くためのメソッドは 2 つあります。Open と OpenEx です。OpenEx メソッドは Open メソッドとほとんど同じですが、呼び出し元が図面を開く方法を指定できる引数を提供する点のみ異なります。  
  
 オブジェクト モデルの詳細については、[Microsoft.Office.Interop.Visio.Documents.Open](HV10070351) メソッドと [Microsoft.Office.Interop.Visio.Documents.OpenEx](HV10071456) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## Visio 図面を開く  
  
#### Visio 図面を開くには  
  
-   Microsoft.Office.Interop.Visio.Documents.Open メソッドを呼び出し、Visio 図面の完全修飾パスを指定します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## 引数を指定して Visio 図面を開く  
  
#### 読み取り専用およびドッキングとして Visio 図面を開くには  
  
-   Microsoft.Office.Interop.Visio.Documents.OpenEx メソッドを呼び出して、Visio 図面の完全修飾パスを指定し、必要な引数を指定します。この例では、ドッキングと読み取り専用の引数を指定しています。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
## コードのコンパイル  
 このコード例で必要な要素は次のとおりです。  
  
-   \[マイ ドキュメント\] フォルダー \(Windows XP 以前の場合\) または \[ドキュメント\] フォルダー \(Windows Vista の場合\) 内の `Test` というディレクトリにある `myDrawing.vsd` という名前の Visio 図面。  
  
## 参照  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [方法: プログラムによって新しい Visio 図面を作成する](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [方法: プログラムによって Visio 図面を閉じる](../vsto/how-to-programmatically-close-visio-documents.md)   
 [方法: プログラムによって Visio 図面を保存する](../vsto/how-to-programmatically-save-visio-documents.md)   
 [方法: プログラムによって Visio 図面を印刷する](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  