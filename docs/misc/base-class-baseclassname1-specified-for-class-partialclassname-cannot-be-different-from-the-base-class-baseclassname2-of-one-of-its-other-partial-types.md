---
title: "クラス &#39;&lt;partialclassname&gt;&#39; に指定された基底クラス &#39;&lt;baseclassname1&gt;&#39; は、その他の partial 型の 1 つである基底クラス &#39;&lt;baseclassname2&gt;&#39; と異なるものにはできません | Microsoft Docs"
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
  - "BC30928"
  - "vbc30928"
helpviewer_keywords: 
  - "BC30928"
ms.assetid: da464f09-1016-4dec-beb7-3202cacd8e1e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# クラス &#39;&lt;partialclassname&gt;&#39; に指定された基底クラス &#39;&lt;baseclassname1&gt;&#39; は、その他の partial 型の 1 つである基底クラス &#39;&lt;baseclassname2&gt;&#39; と異なるものにはできません
1 つのクラスが 2 つ以上の部分宣言で定義されていますが、それらの宣言には、複数の基底クラスが指定された複数の [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement) が含まれています。  
  
 1 つのクラスの定義を複数の部分宣言間で分割すると、コンパイラは、そのすべての部分宣言の和集合としてこのクラスを処理します。 このことは、メンバーだけでなく、実装、継承、およびアクセス レベルにも該当します。  
  
 1 つのクラスで、複数のインターフェイスを実装することはできますが、複数の基底クラスから継承することはできません。 したがって、すべての `Inherits` ステートメントに同じ基底クラスを指定する必要があります。  
  
 **エラー ID:** BC30928  
  
### このエラーを解決するには  
  
-   どのクラスが部分クラスの基底クラスであるかを判断し、異なる基底クラスを指定している `Inherits` ステートメントを部分宣言から削除します。  
  
## 参照  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)