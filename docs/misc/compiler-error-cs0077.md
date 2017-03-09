---
title: "コンパイラ エラー CS0077 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0077"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0077"
ms.assetid: 55d3d290-d172-41a3-b326-ebf5a0a7e81f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0077
as 演算子は参照型または null 許容型で使用してください \('int' は null 非許容の値型です\)。  
  
 [as](/dotnet/csharp/language-reference/keywords/as) 演算子に[値型](/dotnet/csharp/language-reference/keywords/value-types)が渡されました。`as` は [null](/dotnet/csharp/language-reference/keywords/null) を返すことができます。そのため、[参照型](/dotnet/csharp/language-reference/keywords/reference-types)または null 許容型以外は渡せません。 null 許容型の詳細については、「[null 許容型](/dotnet/csharp/programming-guide/nullable-types/index)」を参照してください。  
  
 次の例では CS0077 が生成されます。  
  
```  
// CS0077.cs using System; class C { } struct S { } class M { public static void Main() { object o1, o2; C c; S s; o1 = new C(); o2 = new S(); s = o2 as S;  // CS0077, S is not a reference type. // try the following line instead // c = o1 as C; } }  
```