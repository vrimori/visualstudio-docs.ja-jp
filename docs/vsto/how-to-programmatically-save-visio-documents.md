---
title: "方法: プログラムによって Visio 図面を保存する"
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
  - "図面 [Visual Studio での Office 開発]、保存 (Visio 図面を)"
  - "Visio [Visual Studio での Office 開発]、保存 (Visio 図面を)"
ms.assetid: 1a29ac7e-1da4-4c7a-87a5-d3d16897fe7c
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 方法: プログラムによって Visio 図面を保存する
  Microsoft Office Visio 図面を保存するには、次のようないくつかの方法があります。  
  
-   既存の図面に変更を保存する。  
  
-   新しい図面を保存するか、または新しい名前を付けて図面を保存する。  
  
-   引数を指定して図面を保存する。  
  
 詳細については、[Microsoft.Office.Interop.Visio.Document.Save](HV10071468) メソッド、[Microsoft.Office.Interop.Visio.Document.SaveAs](HV10071469) メソッド、および [Microsoft.Office.Interop.Visio.Document.SaveAsEx](HV10071470) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## 既存の図面を保存する  
  
#### 図面を保存するには  
  
-   前に保存した図面の Microsoft.Office.Tools.Visio.Document クラスの Microsoft.Office.Interop.Visio.Document.Save メソッドを呼び出します。  
  
     このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
    > [!NOTE]  
    >  新しい Visio 図面がまだ保存されていない場合、Microsoft.Office.Interop.Visio.Document.Save メソッドは例外をスローします。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
## 新しい名前を付けて図面を保存する  
 新しい図面を保存するか、または新しい名前を付けて図面を保存するには、Microsoft.Office.Interop.Visio.Document.SaveAs メソッドを使用します。 このメソッドでは、新しいファイル名を指定する必要があります。  
  
#### 作業中の Visio 図面に新しい名前を付けて保存するには  
  
-   ファイル名を含む完全修飾パスを使用して、保存する Microsoft.Office.Tools.Visio.Document の Microsoft.Office.Interop.Visio.Document.SaveAs メソッドを呼び出します。 指定した名前のファイルが既に対象のフォルダー内に存在する場合、そのファイルは警告なしで上書きされます。  
  
     このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## 新しい名前および指定した引数を使用して図面を保存する  
 新しい名前を付けて図面を保存し、適用可能な引数を指定して図面に適用するには、Microsoft.Office.Interop.Visio.Document.SaveAsEx メソッドを使用します。  
  
#### 新しい名前および指定した引数を使用して図面を保存するには  
  
-   ファイル名を含む完全修飾パスを使用して、保存する Microsoft.Office.Tools.Visio.Document の Microsoft.Office.Interop.Visio.Document.SaveAsEx メソッドを呼び出します。 指定した名前のファイルが既に対象のフォルダー内に存在する場合、例外がスローされます。  
  
     次のコード例では、作業中の図面を新しい名前で保存し、その図面を読み取り専用としてマークし、\[直前に使用\] の図面一覧にその図面を表示しています。 このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## コードのコンパイル  
 このコード例で必要な条件は次のとおりです。  
  
-   図面に新しい名前を付けて保存するには、\[マイ ドキュメント\] フォルダー \(Windows XP 以前の場合\) または \[ドキュメント\] フォルダー \(Windows Vista の場合\) 内に `Test` という名前のディレクトリが存在している必要があります。  
  
## 参照  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [方法: プログラムによって新しい Visio 図面を作成する](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [方法: プログラムによって Visio 図面を開く](../vsto/how-to-programmatically-open-visio-documents.md)   
 [方法: プログラムによって Visio 図面を閉じる](../vsto/how-to-programmatically-close-visio-documents.md)   
 [方法: プログラムによって Visio 図面を印刷する](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  