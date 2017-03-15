---
title: "コンパイラ エラー CS0411 | Microsoft Docs"
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
  - "CS0411"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0411"
ms.assetid: 290947c9-10d0-427e-99f2-bff20299d533
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0411
メソッド 'method' の型引数は、使用法から推論することはできません。 型引数を明示的に指定してください。  
  
 このエラーは、型引数を明示的に指定せずにジェネリック メソッドを呼び出し、コンパイラが必要な型引数を推論できない場合に発生します。 このエラーを回避するには、山かっこの中に目的の型引数を追加します。  
  
## 使用例  
 次の例では CS0411 が生成されます。  
  
```  
// CS0411.cs class C { void G<T>() { } public static void Main() { G();  // CS0411 // Try this instead: // G<int>(); } }  
```  
  
## 使用例  
 その他の考えられるエラーには、パラメーターが `null` で、型の情報がない場合があります。  
  
```  
// CS0411b.cs class C { public void F<T>(T t) where T : C { } public static void Main() { C c = new C(); c.F(null);  // CS0411 } }  
```