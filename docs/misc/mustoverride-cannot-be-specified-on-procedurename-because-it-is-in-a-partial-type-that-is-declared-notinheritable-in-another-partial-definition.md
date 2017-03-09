---
title: "別の部分宣言で &#39;NotInheritable&#39; と宣言された部分型であるため、&#39;MustOverride&#39; を &#39;&lt;procedurename&gt;&#39; で指定することはできません | Microsoft Docs"
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
  - "vbc30927"
  - "BC30927"
helpviewer_keywords: 
  - "BC30927"
ms.assetid: 5798dfda-3d7b-4f30-9715-40cbf52d6dc4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 別の部分宣言で &#39;NotInheritable&#39; と宣言された部分型であるため、&#39;MustOverride&#39; を &#39;&lt;procedurename&gt;&#39; で指定することはできません
複数の部分宣言で定義されたクラスの内部でプロシージャまたはプロパティが `MustOverride` として宣言されていますが、部分定義の 1 つでそのクラスに対して `NotInheritable` が指定されています。  
  
 1 つのクラスの定義を複数の部分宣言間で分割すると、コンパイラは、そのすべての部分宣言の和集合としてこのクラスを処理します。 このことは、メンバーだけでなく、実装、継承、アクセス レベルにも該当します。  
  
 プロシージャまたはプロパティをオーバーライドするには、クラスが基底クラスを継承していることが必要です。 したがって、基底クラスのプロシージャやプロパティに `MustOverride` を指定するには、そのクラスに `MustInherit` を指定する必要があります。`MustInherit` と `NotInheritable` は互いに矛盾しているので、同じクラスにこの 2 つを指定することはできません。  
  
 **エラー ID:** BC30927  
  
### このエラーを解決するには  
  
-   プロパティまたはプロシージャをオーバーライドする必要がある場合は、`NotInheritable` キーワードが現れる部分宣言から、このキーワードを削除します。  
  
-   クラスを `NotInheritable` にする必要がある場合は、プロシージャまたはプロパティから `MustOverride` キーワードを削除します。 クラスは継承できないため、オーバーライドすることはできません。  
  
## 参照  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)