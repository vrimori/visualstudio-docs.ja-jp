---
title: "方法: プログラムによって Document プロパティを Word の表に読み込む | Microsoft Docs"
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
  - "ドキュメントのプロパティ, 挿入 (Word テーブルに)"
  - "ドキュメント [Visual Studio での Office 開発], ドキュメントのプロパティ"
ms.assetid: 7ed65a3d-58ed-43b3-92d6-dc10a2c331db
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 方法: プログラムによって Document プロパティを Word の表に読み込む
  次の例ではドキュメントの先頭に Microsoft Office Word の表を作成し、ホスト ドキュメントのプロパティのデータをそこに読み込みます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## ドキュメント レベルのカスタマイズでの表データの読み込み  
  
#### 表を作成し、ドキュメントのプロパティ データをそこに読み込むには  
  
1.  ドキュメントの先頭に、範囲を設定します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#90](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#90)]
     [!code-vb[Trin_VstcoreWordAutomation#90](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#90)]  
  
2.  表のタイトルを挿入し、段落記号を含めます。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#91](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#91)]
     [!code-vb[Trin_VstcoreWordAutomation#91](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#91)]  
  
3.  ドキュメントの範囲に表を追加します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#92](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#92)]
     [!code-vb[Trin_VstcoreWordAutomation#92](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#92)]  
  
4.  表の書式を設定し、スタイルを適用します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#93](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#93)]
     [!code-vb[Trin_VstcoreWordAutomation#93](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#93)]  
  
5.  セルにドキュメントのプロパティを挿入します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#94](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#94)]
     [!code-vb[Trin_VstcoreWordAutomation#94](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#94)]  
  
 次の例は、全手順を示しています。  このコードを使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#89](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#89)]
 [!code-vb[Trin_VstcoreWordAutomation#89](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#89)]  
  
## VSTO アドインでの表データの読み込み  
  
#### 表を作成し、ドキュメントのプロパティ データをそこに読み込むには  
  
1.  ドキュメントの先頭に、範囲を設定します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#90](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#90)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#90](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#90)]  
  
2.  表のタイトルを挿入し、段落記号を含めます。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#91](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#91)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#91](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#91)]  
  
3.  ドキュメントの範囲に表を追加します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#92](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#92)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#92](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#92)]  
  
4.  表の書式を設定し、スタイルを適用します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#93](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#93)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#93](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#93)]  
  
5.  セルにドキュメントのプロパティを挿入します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#94](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#94)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#94](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#94)]  
  
 次の例は、全手順を示しています。  このコードを使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#89](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#89)]
 [!code-vb[Trin_VstcoreWordAutomationAddIn#89](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#89)]  
  
## 参照  
 [方法: プログラムによって Word の表を作成する](../vsto/how-to-programmatically-create-word-tables.md)   
 [方法: プログラムによって Word の表のセルにテキストと書式設定を追加する](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [方法: プログラムによって Word の表に行と列を追加する](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  