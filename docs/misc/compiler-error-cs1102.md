---
title: "コンパイラ エラー CS1102 | Microsoft Docs"
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
  - "CS1102"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1102"
ms.assetid: 7de798d4-1b4b-4842-ae43-9bc83e6dc9a3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1102
パラメーター修飾子 'out' は 'this' と共に使用できません  
  
 `this` キーワードは、静的メソッドの最初のパラメーターを修飾するとき、そのメソッドが拡張メソッドであることをコンパイラに通知します。 拡張メソッドの最初のパラメーターでは、その他の修飾子は必要ないか、または許可されません。  
  
### このエラーを解決するには  
  
1.  最初のパラメーターから、承認されていない修飾子を削除します。  
  
## 使用例  
 次の例では CS1102 が生成されます。  
  
```  
// cs1102.cs // Compile with: /target:library. public static class Extensions { // No type parameters. public static void Test(this out int i) {} // CS1102 //Single type parameter public static void Test<T>(this out T t) {}// CS1102 //Multiple type parameters public static void Test<T,U,V>(this out U u) {}// CS1102 }  
```  
  
## 参照  
 [拡張メソッド](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [this](/dotnet/csharp/language-reference/keywords/this)   
 [out](/dotnet/csharp/language-reference/keywords/out)