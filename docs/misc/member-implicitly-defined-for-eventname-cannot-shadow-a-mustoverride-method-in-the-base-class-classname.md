---
title: "&lt;eventname&gt; で暗黙のうちに定義された &#39;&lt;member&gt;&#39; が、基底 &lt;class&gt; &#39;&lt;classname&gt;&#39; の &#39;MustOverride&#39; メソッドをシャドウすることはできません。 | Microsoft Docs"
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
  - "vbc31413"
  - "bc31413"
helpviewer_keywords: 
  - "BC31413"
ms.assetid: 071706ce-a394-48b6-9afa-751cb50b2576
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;eventname&gt; で暗黙のうちに定義された &#39;&lt;member&gt;&#39; が、基底 &lt;class&gt; &#39;&lt;classname&gt;&#39; の &#39;MustOverride&#39; メソッドをシャドウすることはできません。
指定されたイベントが、`MustOverride` 修飾子によって宣言されたメソッドとして同じ名前を持つメンバーを暗黙的に宣言します。  
  
 **エラー ID:** BC31413  
  
### このエラーを解決するには  
  
-   基底クラスのメソッドから `MustOverride` 修飾子を削除するか、またはプロパティかメソッドに一意の名前を指定します。  
  
## 参照  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)