---
title: "方法: Visio 図面の図形をプログラムによってコピーして貼り付ける"
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
  - "図形 [Visual Studio での Office 開発]、コピーと貼り付け (Visio 図形の)"
  - "Visio [Visual Studio での Office 開発]、コピーと貼り付け (Visio 図形の)"
ms.assetid: 762d95cf-2d5c-4dea-988b-8f4da88fa1f1
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 方法: Visio 図面の図形をプログラムによってコピーして貼り付ける
  プログラムを使用してドキュメントの 1 つのページ上の図形をコピーし、同じドキュメント内の新しいページに貼り付けることができます。 貼り付け先として、既定の場所 \(アクティブ ウィンドウの中央\)、または元のページと同じ座標位置を選択できます。  
  
## 図形のコピーと貼り付け  
 オブジェクト モデルの詳細については、[Microsoft.Office.Interop.Visio.Shape.DrawRectangle](HV10070304)、[Microsoft.Office.Interop.Visio.Shape.DrawOval](HV10070300)、[Microsoft.Office.Interop.Visio.Shape.Copy](HV10070291)、および [Microsoft.Office.Interop.Visio.Shape.Paste](HV10070437) メソッドと [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](HV10071835) フラグの VBA リファレンス ドキュメントを参照してください。  
  
#### 別のページの中央に図形をコピーするには  
  
-   次の例では、最初のページの図形をコピーし、2 番目のページの中央に貼り付ける方法を示します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#14)]  
  
## 図形をコピーし同じ位置に貼り付け  
 オブジェクト モデルの詳細については、[Microsoft.Office.Interop.Visio.Shape.DrawRectangle](HV10070304)、[Microsoft.Office.Interop.Visio.Shape.DrawOval](HV10070300)、[Microsoft.Office.Interop.Visio.Shape.Copy](HV10070291)、および [Microsoft.Office.Interop.Visio.Shape.Paste](HV10070437) メソッドと [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](HV10071835) フラグの VBA リファレンス ドキュメントを参照してください。  
  
 貼り付けた情報の形式を制御し、\(必要に応じて\) ソース ファイル \(たとえば、Microsoft Office Word ドキュメントなど\) へのリンクを確立する必要がある場合は、PasteSpecial メソッドを使用します。  
  
#### 図形と図形の位置を別のページにコピーするには  
  
-   次の例では、最初のページの図形をコピーし、2 番目のページの同じ座標位置に貼り付ける方法を示します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#15)]  
  
## 参照  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [Visio の図形の操作](../vsto/working-with-visio-shapes.md)   
 [方法: プログラムによって Visio 図面に図形を追加する](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  