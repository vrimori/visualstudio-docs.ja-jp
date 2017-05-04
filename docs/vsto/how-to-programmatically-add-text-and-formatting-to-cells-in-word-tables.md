---
title: "方法: プログラムによって Word の表のセルにテキストと書式設定を追加する | Microsoft Docs"
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
  - "セル, 追加 (テキストと書式設定を)"
  - "書式設定 [Visual Studio での Office 開発]"
  - "テーブル [Visual Studio での Office 開発], 追加 (テキストと書式設定を)"
  - "テキスト [Visual Studio での Office 開発], 追加 (Word テーブルに)"
ms.assetid: 3df6492a-dc9c-43ac-8fc3-0f944edd88b2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 方法: プログラムによって Word の表のセルにテキストと書式設定を追加する
  表はセルの集まりで構成されます。  個々の <xref:Microsoft.Office.Interop.Word.Cell> オブジェクトが表内の 1 つのセルを表します。  各セルは、表内の場所を指定して参照します。  次の例では、表の最初の行の最初の列のセルを参照し、そのセルにテキストを追加して、書式を適用します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### セルにテキストと書式設定を追加するには  
  
1.  表内の場所を指定してセルを参照し、そのセルにテキストを追加して書式を適用します。  
  
     次のコード例はドキュメント レベルのカスタマイズで使用できます。  このコード例を使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomation#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#97)]  
  
     次のコード例は VSTO アドインで使用できます。  この例ではアクティブ ドキュメントを使用します。  この例を使用するには、プロジェクトの `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#97)]  
  
## 参照  
 [方法: プログラムによって Word の表を作成する](../vsto/how-to-programmatically-create-word-tables.md)   
 [方法: プログラムによって Word の表に行と列を追加する](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [方法: プログラムによって Document プロパティを Word の表に読み込む](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  