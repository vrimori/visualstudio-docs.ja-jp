---
title: "方法: プログラムによって文書でスペル チェックを行う"
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
  - "ドキュメント [Visual Studio での Office 開発], チェック (スペルを)"
  - "スペル チェック, ドキュメント"
ms.assetid: 5bbe3a8d-fc65-4f57-bd63-5bb549dbc4bd
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 方法: プログラムによって文書でスペル チェックを行う
  ドキュメント内でスペル チェックを実行するには、<xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> メソッドを使用します。  このメソッドは、指定されたパラメーターのスペルが正しいかどうかを示すブール値を返します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### スペルチェックを実行し、メッセージ ボックスに結果を表示するには  
  
1.  <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> メソッドを呼び出し、スペルの誤りをチェックするテキストの範囲を渡します。  このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#113](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#113)]
     [!code-vb[Trin_VstcoreWordAutomation#113](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#113)]  
  
## 参照  
 [方法: プログラムによって文書に複数の範囲を定義して選択する](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  