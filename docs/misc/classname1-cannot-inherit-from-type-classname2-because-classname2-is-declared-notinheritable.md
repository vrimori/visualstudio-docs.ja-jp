---
title: "&#39;&lt;classname2&gt;&#39; が &#39;NotInheritable&#39; として宣言されているため、&#39;&lt;classname1&gt;&#39; は &lt;type&gt; &#39;&lt;classname2&gt;&#39; から継承できません。 | Microsoft Docs"
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
  - "vbc30299"
  - "bc30299"
helpviewer_keywords: 
  - "BC30299"
ms.assetid: 627d50f5-9e75-495d-93f7-50096ba2ea08
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;classname2&gt;&#39; が &#39;NotInheritable&#39; として宣言されているため、&#39;&lt;classname1&gt;&#39; は &lt;type&gt; &#39;&lt;classname2&gt;&#39; から継承できません。
クラスが別のクラスから継承しようとしていますが、目的の基底クラスは `NotInheritable` として指定されています。`NotInheritable` クラスは、主に意図しない派生を防ぐために使用されます。  
  
 **エラー ID:** BC30299  
  
### このエラーを解決するには  
  
-   `NotInheritable` キーワードを目的の基底クラスの定義から削除するか、`Inherits` ステートメントを削除します。  
  
## 参照  
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)   
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)