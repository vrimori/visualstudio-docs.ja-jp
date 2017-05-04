---
title: "方法: プログラムによって新しい Visio 図面を作成する | Microsoft Docs"
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
  - "Visio [Visual Studio での Office 開発]、作成 (Visio 図面を)"
  - "図面 [Visual Studio での Office 開発]、作成 (Visio 図面を)"
ms.assetid: a0294d4c-be49-4cd0-b22e-3ec7568f3ec7
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 方法: プログラムによって新しい Visio 図面を作成する
  Microsoft Office Visio 描画図面を新規に作成する場合、開いている Visio 図面の Microsoft.Office.Interop.Visio.Documents コレクションにその図面を追加します。 これにより、Microsoft.Office.Interop.Visio.Documents.Add メソッドで新しい Visio 描画図面が作成されます。 詳細については、[Microsoft.Office.Interop.Visio.Documents.Add](HV10069241) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## 新しい空白の図面の作成  
  
#### 新しい図面を作成するには  
  
-   Microsoft.Office.Interop.Visio.Documents.Add メソッドを使用して、テンプレートに基づかない新しい空白の図面を作成します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#1)]  
  
## 既存の図面をコピーして図面を作成する  
 Microsoft.Office.Interop.Visio.Documents.Add メソッドは、既存の Visio 図面をコピーして新しい図面を作成できます。 図のファイル名と完全修飾パスを指定する必要があります。  
  
#### 既存の図面をコピーして新しい図面を作成するには  
  
-   Microsoft.Office.Interop.Visio.Documents.Add メソッドを呼び出して、Visio 図面のパスを指定します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#2)]  
  
## 既存のステンシルをコピーしてステンシルを作成する  
 [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241) メソッドは、既存の Visio ステンシルをコピーして新しいステンシルを作成できます。 ステンシルのファイル名と完全修飾パスを指定する必要があります。  
  
#### 既存のステンシルをコピーして新しいステンシルを作成するには  
  
-   Microsoft.Office.Interop.Visio.Documents.Add メソッドを呼び出して、ステンシルのパスを指定します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## 既存のテンプレートに基づいて図面を作成する  
 Microsoft.Office.Interop.Visio.Documents.Add メソッドは、既存の Visio テンプレート \(.vst ファイル\) に基づいて、新しい図面 \(.vsd ファイル\) を作成できます。 このメソッドは、テンプレート ワークスペースの一部である、ステンシル、スタイル、および設定をコピーします。 テンプレートのファイル名と完全修飾パスを指定する必要があります。  
  
#### 既存のテンプレートに基づいて新しい図面を作成するには  
  
-   Microsoft.Office.Interop.Visio.Documents.Add メソッドを呼び出して、テンプレートのパスを指定します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## コードのコンパイル  
 このコード例で必要な要素は次のとおりです。  
  
-   \[マイ ドキュメント\] フォルダー \(Windows XP 以前の場合\) または \[ドキュメント\] フォルダー \(Windows Vista の場合\) 内の `Test` というディレクトリにある `myDrawing.vsd` という名前の Visio 図面。  
  
-   \[マイ ドキュメント\] フォルダー \(Windows XP 以前の場合\) または \[ドキュメント\] フォルダー \(Windows Vista の場合\) 内の `Test` というディレクトリにある `myStencil.vss` という名前の Visio 図面。  
  
-   \[マイ ドキュメント\] フォルダー \(Windows XP 以前の場合\) または \[ドキュメント\] フォルダー \(Windows Vista の場合\) 内の `Test` というディレクトリにある `myTemplate.vst` という名前の Visio 図面。  
  
## 参照  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [方法: プログラムによって Visio 図面を開く](../vsto/how-to-programmatically-open-visio-documents.md)   
 [方法: プログラムによって Visio 図面を閉じる](../vsto/how-to-programmatically-close-visio-documents.md)   
 [方法: プログラムによって Visio 図面を保存する](../vsto/how-to-programmatically-save-visio-documents.md)   
 [方法: プログラムによって Visio 図面を印刷する](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  