---
title: "&#39;AddHandler&#39;、&#39;RemoveHandler&#39; または &#39;RaiseEvent&#39; メソッドの &#39;Return&#39; ステートメントは値を返すことができません | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30940"
  - "vbc30940"
helpviewer_keywords: 
  - "BC30940"
ms.assetid: 0e4d037a-2d20-40e4-8ead-6d709d1c9c7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddHandler&#39;、&#39;RemoveHandler&#39; または &#39;RaiseEvent&#39; メソッドの &#39;Return&#39; ステートメントは値を返すことができません
`Custom Event` 宣言内の `AddHandler`、`RemoveHandler`、`RaiseEvent` の各メソッドには、それぞれのメソッドを終了する `Return` ステートメントを含めることができます。 ただし、いずれのメソッドも値を返すことができないため、`Return` ステートメントでは戻り値を指定できません。  
  
 **エラー ID:** BC30940  
  
### このエラーを解決するには  
  
-   `Return` ステートメントに続く式を削除します。  
  
## 参照  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- 削除](http://msdn.microsoft.com/ja-jp/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- 削除](http://msdn.microsoft.com/ja-jp/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- 削除](http://msdn.microsoft.com/ja-jp/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Return Statement](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)