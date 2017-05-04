---
title: "方法: プログラムによって Visio 図面に図形を追加する | Microsoft Docs"
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
  - "Visio [Visual Studio での Office 開発]、追加 (Visio 図形を)"
  - "図形 [Visual Studio での Office 開発]、追加 (Visio 図形を)"
ms.assetid: 29613237-88f5-41a7-9e13-cfa177f41221
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 方法: プログラムによって Visio 図面に図形を追加する
  ステンシルからマスターを取得し、図形をアクティブ ページにドロップすると、Microsoft Office Visio 図面に図形を追加できます。  
  
 詳しくは、[Microsoft.Office.Interop.Visio.Documents.Add](HV10069241) メソッド、[Microsoft.Office.Interop.Visio.Application.ActivePage](HV10069528) プロパティ、[Microsoft.Office.Interop.Visio.Page.Drop](HV10070273) メソッドの VBA リファレンス ドキュメントをご覧ください。  
  
## Visio 図面への図形の追加  
  
#### Visio 図面に図形を追加するには  
  
-   ドキュメントをアクティブにして、Documents.Masters コレクションからマスターを取得し、アクティブなドキュメントに図形をドロップします。 インデックスまたはマスターの名前を使用して、マスターを取得できます。  
  
     次のコード例は、空の Visio 図面を作成し、**\[基本図形\]** ステンシルをドッキングした状態で図面を開きます。 次に、このコードはいくつかの図形を取得し、それらをアクティブ ページにドロップします。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
## 参照  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [Visio の図形の操作](../vsto/working-with-visio-shapes.md)   
 [方法: Visio 図面の図形をプログラムによってコピーして貼り付ける](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  