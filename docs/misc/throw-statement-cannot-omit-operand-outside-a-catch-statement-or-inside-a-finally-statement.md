---
title: "&#39;Throw&#39; ステートメントでは、&#39;Catch&#39; ステートメントの外側、または &#39;Finally&#39; ステートメントの内側にあるオペランドを省略できません | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30666"
  - "bc30666"
helpviewer_keywords: 
  - "BC30666"
ms.assetid: a208a6ea-0e36-4bf1-8984-4de1a0e38a2a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Throw&#39; ステートメントでは、&#39;Catch&#39; ステートメントの外側、または &#39;Finally&#39; ステートメントの内側にあるオペランドを省略できません
`Catch` ステートメントの外側にある `Throw` ステートメントでは、例外オブジェクトの名前を指定する必要があります。  
  
 **エラー ID:** BC30666  
  
### このエラーを解決するには  
  
1.  `System.Exception` から派生した例外オブジェクトの名前を指定します。  
  
2.  `Throw` ステートメントが `Catch` ブロックの内側に配置されるようにコードを再構築します。  
  
## 参照  
 [Throw Statement](/dotnet/visual-basic/language-reference/statements/throw-statement)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Visual Basic での例外クラス](http://msdn.microsoft.com/ja-jp/9aac396f-34ca-4afb-8e6c-e523cb690ba9)   
 [Visual Basic での例外とエラー処理](http://msdn.microsoft.com/ja-jp/3e351e73-cf23-40ab-8b60-05794160529e)