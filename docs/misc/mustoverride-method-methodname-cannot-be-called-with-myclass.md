---
title: "&#39;MustOverride&#39; メソッド &#39;&lt;methodname&gt;&#39; を、&#39;MyClass&#39; で呼び出すことはできません | Microsoft Docs"
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
  - "bc30614"
  - "vbc30614"
helpviewer_keywords: 
  - "BC30614"
ms.assetid: fc57af41-1552-46d1-9727-341f1835e661
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MustOverride&#39; メソッド &#39;&lt;methodname&gt;&#39; を、&#39;MyClass&#39; で呼び出すことはできません
`MyClass` は、`Me` と同等ですが、そのすべてのメソッド呼び出しは、呼び出されるメソッドが `NotOverridable` であるかのように扱われます。  
  
 **エラー ID:** BC30614  
  
### このエラーを解決するには  
  
-   `MustOverride` 修飾子を削除するか、または基底クラスでメソッドを宣言し、そのクラスを継承およびオーバーライドします。  
  
## 参照  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)