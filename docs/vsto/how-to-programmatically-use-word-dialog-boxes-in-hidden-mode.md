---
title: "方法: プログラムによって Word のダイアログ ボックスを非表示モードで使用する"
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
  - "ダイアログ ボックス, 非表示モード (Word の)"
  - "非表示のダイアログ ボックス"
  - "Word [Visual Studio での Office 開発], ダイアログ ボックス"
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 方法: プログラムによって Word のダイアログ ボックスを非表示モードで使用する
  Microsoft Office Word の組み込みダイアログ ボックスをユーザーには表示せずに呼び出すことによって、1 回のメソッド呼び出しで複雑な操作を実行できます。  これを行うには、<xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> メソッドは呼び出さずに、<xref:Microsoft.Office.Interop.Word.Dialog> オブジェクトの <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> メソッドを使用します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 例  
 以下のコード例では、非表示モードの **\[ページ設定\]** ダイアログ ボックスを使用して、ユーザー入力を使用せずに複数のページ設定プロパティを設定する方法を示します。  この例では、<xref:Microsoft.Office.Interop.Word.Dialog> オブジェクトを使用して、カスタム ページ サイズを設定しています。  上部余白や下部余白などの特定のページ設定値は、<xref:Microsoft.Office.Interop.Word.Dialog> オブジェクトの遅延バインディング プロパティとして使用できます。  これらのプロパティは、実行時に Word によって動的に作成されます。  
  
 **Option Strict** がオフの Visual Basic プロジェクトまたは [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を対象とする Visual C\# プロジェクトでこのタスクを実行する方法を次の例に示します。  これらのプロジェクトでは、Visual Basic コンパイラおよび Visual C\# コンパイラの遅延バインディング機能を使用できます。  このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスから実行します。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#123](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#123)]
 [!code-vb[Trin_VstcoreWordAutomation#123](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#123)]  
  
 次の例に **Option Strict** がオンのVisual Basicプロジェクトでこのタスクを実行する方法を示します。  これらのプロジェクトでは、遅延バインディング プロパティにアクセスするにはリフレクションを使用する必要があります。  このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスから実行します。  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#104)]  
  
## 参照  
 [方法: プログラムによって Word の組み込みダイアログ ボックスを使用する](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [Office ソリューションの遅延バインディング](../vsto/late-binding-in-office-solutions.md)   
 [リフレクション &#40;C&#35; および Visual Basic&#41;](../Topic/Reflection%20(C%23%20and%20Visual%20Basic).md)  
  
  