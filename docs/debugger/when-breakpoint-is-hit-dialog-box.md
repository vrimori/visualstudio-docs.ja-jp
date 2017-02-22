---
title: "[ブレークポイントのヒット時] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.whenbreakpointishit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# [ブレークポイントのヒット時] ダイアログ ボックス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このダイアログ ボックスでは、ブレークポイントにヒットしたときに発生するアクションをカスタマイズできます。  
  
## UIElement の一覧  
 **\[メッセージを表示する\]**  
 DebuggerDisplay 構文を使用してメッセージを出力します。  詳細については、「[DebuggerDisplay 属性を使用します](../debugger/using-the-debuggerdisplay-attribute.md)」を参照してください。  
  
 このテキストボックスは、$ADDRESS などの特殊なキーワードもサポートしています。これらのキーワードはキーワード自身が使用することも、DebuggerDisplay 式の中かっこ \({}\) 内で使用することもできます。  使用できるキーワードはダイアログ ボックスに一覧表示されます。  
  
 **\[続けて実行する\]**  
 このコントロールは、**\[メッセージを表示する\]** が選択されている場合にだけ有効になります。  このコントロールを選択すると、ブレークポイントにヒットしたときに、これを中断するポイントとしてではなく、プログラムの実行をトレースするためのトレースポイントとして使用できます。  
  
## 参照  
 [ブレークポイントの使用](../debugger/using-breakpoints.md)   
 [DebuggerDisplay 属性を使用します](../debugger/using-the-debuggerdisplay-attribute.md)