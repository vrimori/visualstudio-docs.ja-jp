---
title: "&#39;&lt;typename&gt;&#39; で、&lt;type&gt; &#39;&lt;typename&gt;&#39; のプロパティ &#39;&lt;propertyname&gt;&#39; に対して暗黙的に宣言された &#39;MustOverride&#39; メソッドをシャドウすることはできません | Microsoft Docs"
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
  - "bc31416"
  - "vbc31416"
helpviewer_keywords: 
  - "BC31416"
ms.assetid: a52aee3c-a19e-412d-bb91-ef1b79e8675f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; で、&lt;type&gt; &#39;&lt;typename&gt;&#39; のプロパティ &#39;&lt;propertyname&gt;&#39; に対して暗黙的に宣言された &#39;MustOverride&#39; メソッドをシャドウすることはできません
指定したメソッド名が、基底クラスのプロパティによって暗黙的に生成された `MustOverride` メソッドと競合しています。 たとえば、`Prop1` という名前のプロパティを宣言した場合、コンパイラは暗黙的なプロシージャ `get_Prop1` と `set_Prop1` を生成します。  
  
 **エラー ID:** BC31416  
  
### このエラーを解決するには  
  
1.  メソッドに一意の名前を付けます。  
  
2.  基底クラスのプロパティから `MustOverride` 修飾子を削除します。  
  
## 参照  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)