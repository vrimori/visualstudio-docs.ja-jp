---
title: "&lt;type1&gt; &#39;&lt;typename1&gt;&#39; は、&lt;type2&gt; &#39;&lt;typename2&gt;&#39; のイベント &#39;&lt;eventname&gt;&#39; に対して暗黙的に宣言されたメンバーと競合しています | Microsoft Docs"
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
  - "vbc31061"
  - "bc31061"
helpviewer_keywords: 
  - "BC31061"
ms.assetid: de5b1121-8c8f-4aba-a3e7-1e3e60df0dc5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt; &#39;&lt;typename1&gt;&#39; は、&lt;type2&gt; &#39;&lt;typename2&gt;&#39; のイベント &#39;&lt;eventname&gt;&#39; に対して暗黙的に宣言されたメンバーと競合しています
型メンバーの名前が、イベントに対して暗黙的に作成されたメンバーの名前と競合しています。 イベントは、いくつかの暗黙的な変数を暗黙的に作成します。 たとえば、宣言 `Event X` は `XEventHandler`、`XEvent`、`add_X`、および `remove_X` という名前を暗黙的に宣言します。  
  
 **エラー ID:** BC31061  
  
### このエラーを解決するには  
  
-   明示的に宣言したメンバーの名前を変更して、名前の競合を解決します。  
  
## 参照  
 [NotInBuild: Visual Basic における宣言ステートメント](http://msdn.microsoft.com/ja-jp/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)