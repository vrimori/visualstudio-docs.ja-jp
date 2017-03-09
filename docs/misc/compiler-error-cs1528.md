---
title: "コンパイラ エラー CS1528 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1528"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1528"
ms.assetid: 38aabc5c-b32f-4bea-a585-c4212f42751d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1528
; または \= を指定してください \(宣言の中にコンストラクター引数は指定できません\)  
  
 クラスに対する参照が、クラスに対するオブジェクトが生成されているときのように行われました。 たとえば、変数をコンストラクターに渡そうとしました。[new](/dotnet/csharp/language-reference/keywords/new) 演算子を使用して、クラスのオブジェクトを作成してください。  
  
 次の例では CS1528 が生成されます。  
  
```  
// CS1528.cs using System; public class B { public B(int i) { _i = i; } public void PrintB() { Console.WriteLine(_i); } private int _i; } public class mine { public static void Main() { B b(3);   // CS1528, reference is not an object // try one of the following // B b; // or // B bb = new B(3); // bb.PrintB(); } }  
```