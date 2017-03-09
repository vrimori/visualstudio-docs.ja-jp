---
title: "コンパイラ エラー CS0542 | Microsoft Docs"
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
  - "CS0542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0542"
ms.assetid: 68a89948-8b56-4cd5-95e2-0df7fcad50ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0542
'user\-defined type' : メンバー名をそれを囲む型の名前と同じにすることはできません  
  
 クラスまたは構造体のメンバーは、メンバーがコンストラクターでない限り、クラスまたは構造体と同じ名前にすることはできません。  
  
 次の例では CS0542 が生成されます。  
  
```c#  
// CS0542.cs class C { public int C; }  
```  
  
 このエラーは、コンストラクターに誤って戻り値の型を指定したことにより、コンストラクターが事実上、通常のメソッドとなる場合に発生する可能性があります。 次の例では、`F` が戻り値の型を含むことから、コンストラクターではなくメソッドとなるため、CS0542 が生成されます。  
  
```c#  
// CS0542.cs class F { // Remove void from F() to resolve the problem. void F()   // CS0542, same name as the class { } } class MyClass { public static void Main() { } }  
```  
  
 クラスの名前が 'Item' で、`this` として宣言されたインデクサーが含まれている場合、このエラーが発生する可能性があります。 既定のインデクサーには、出力コードで 'Item' の名前が指定されるため、競合が発生します。  
  
```c#  
// CS0542b.cs class Item { public int this[int i]  // CS0542 { get { return 0; } } } class CMain { public static void Main() { } }  
```