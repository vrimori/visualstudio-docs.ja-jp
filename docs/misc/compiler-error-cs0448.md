---
title: "コンパイラ エラー CS0448 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0448"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0448"
ms.assetid: f577ab4c-1c8c-4a10-80a8-9ba9f66c3d25
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0448
\+\+ または \-\- 演算子の戻り値の型は、それを含む型であるか、またはそれを含む型から派生しなければなりません  
  
 `++` または `--` 演算子をオーバーライドする場合、含む型と同じ型か、または含む型から派生した型を返す必要があります。  
  
## 使用例  
 次の例では CS0448 が生成されます。  
  
```  
// CS0448.cs class C5 { public static int operator ++(C5 c) { return null; }   // CS0448 public static C5 operator --(C5 c) { return null; }   // OK public static void Main() {} }  
```  
  
## 使用例  
 次の例では CS0448 が生成されます。  
  
```  
// CS0448_b.cs public struct S { public static S? operator ++(S s) { return new S(); }   // CS0448 public static S? operator --(S s) { return new S(); }   // CS0448 } public struct T { // OK public static T operator --(T t) { return new T(); } public static T operator ++(T t) { return new T(); } public static T? operator --(T? t) { return new T(); } public static T? operator ++(T? t) { return new T(); } public static void Main() {} }  
```