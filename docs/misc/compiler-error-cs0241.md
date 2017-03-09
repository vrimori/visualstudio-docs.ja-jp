---
title: "コンパイラ エラー CS0241 | Microsoft Docs"
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
  - "CS0241"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "メソッド パラメーターの既定値"
  - "既定値、パラメーター値"
  - "既定値、メソッド パラメーター値"
  - "既定のパラメーター値"
  - "CS0241"
ms.assetid: be31b194-3de5-4aab-b23a-6cf790f940ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0241
既定のパラメーター指定子は使用できません  
  
 [メソッド パラメーター](/dotnet/csharp/language-reference/keywords/method-parameters)には既定値を指定できません。 同じ効果を得るには、メソッド オーバーロードを使用します。 詳細については、「[パラメーターの引き渡し](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)」を参照してください。  
  
## 使用例  
 次の例では CS0241 が生成されます。 また、次の例では、既定の引数を持つメソッドをオーバーロードを使用してシミュレートする方法を示します。  
  
```  
// CS0241.cs public class A { public void Test(int i = 9) {}   // CS0241 } public class B { public void Test() { Test(9); } public void Test(int i)  {} } public class C { public static void Main() { B x = new B(); x.Test(); } }  
```