---
title: "方法: プログラムによって Word の検索オプションを設定する | Microsoft Docs"
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
  - "ドキュメント [Visual Studio での Office 開発], 検索オプション"
  - "検索, Word オプション"
  - "設定, Word 検索オプション"
  - "Word, 検索オプション"
ms.assetid: 4412b4e8-2868-4afb-a593-983603ef9b02
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 方法: プログラムによって Word の検索オプションを設定する
  Microsoft Office Word 文書内の選択範囲に対して検索オプションを設定するには、2 種類の方法があります。  
  
-   <xref:Microsoft.Office.Interop.Word.Find> オブジェクトの個々のプロパティを設定する方法  
  
-   <xref:Microsoft.Office.Interop.Word.Find> オブジェクトの <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> メソッドの引数を使用する方法  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Find オブジェクトのプロパティの使用  
 次のコードでは、<xref:Microsoft.Office.Interop.Word.Find> オブジェクトのプロパティを設定して、現在の選択範囲内でテキストを検索します。  前方向への検索、折り返し、検索テキストなどの検索条件は、<xref:Microsoft.Office.Interop.Word.Find> オブジェクトのプロパティであることに注意してください。  
  
 C\# コードを記述する場合は、<xref:Microsoft.Office.Interop.Word.Find.Execute%2A> メソッドのパラメーターと同じプロパティを指定する必要があるため、<xref:Microsoft.Office.Interop.Word.Find> オブジェクトの各プロパティを設定する方法は効率的ではありません。  このため、この例は Visual Basic コードでのみ用意されています。  
  
#### Find オブジェクトを使用して検索オプションを設定するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Find> オブジェクトのプロパティを設定して、選択範囲の中で **find me** というテキストを前方向に検索します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#76)]  
  
## Execute メソッドの引数の使用  
 次のコードでは、<xref:Microsoft.Office.Interop.Word.Find> オブジェクトの <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> メソッドを使用して、現在の選択範囲内でテキストを検索します。  前方向への検索、折り返し、検索テキストなどの検索条件は、<xref:Microsoft.Office.Interop.Word.Find.Execute%2A> メソッドのパラメーターとして渡されることに注意してください。  
  
#### Execute メソッドの引数を使用して検索オプションを設定するには  
  
1.  検索条件を <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> メソッドのパラメーターとして渡して、選択範囲の中で "**find me**" というテキストを前方向に検索します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#77](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#77)]
     [!code-vb[Trin_VstcoreWordAutomation#77](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#77)]  
  
## 参照  
 [方法: プログラムによって文書内のテキストを検索および置換する](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [方法: 文書で見つかった項目をプログラムによってループする](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [方法: プログラムによって検索後に選択範囲を復元する](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  