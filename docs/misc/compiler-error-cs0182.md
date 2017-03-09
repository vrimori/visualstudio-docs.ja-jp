---
title: "コンパイラ エラー CS0182 | Microsoft Docs"
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
  - "CS0182"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0182"
ms.assetid: a9e97bb8-f06e-499f-aadf-26abc2082f98
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0182
属性引数は、定数式、typeof 式、または属性パラメーター型の配列の作成式でなければなりません。  
  
 どの種類の引数を属性に使用できるかについて、特定の制限が適用されます。 エラー メッセージに示された制限に加えて、次の型を属性引数として使用できないことに注意してください。  
  
-   [sbyte](/dotnet/csharp/language-reference/keywords/sbyte)  
  
-   [ushort](/dotnet/csharp/language-reference/keywords/ushort)  
  
-   [uint](/dotnet/csharp/language-reference/keywords/uint)  
  
-   [ulong](/dotnet/csharp/language-reference/keywords/ulong)  
  
-   [decimal](/dotnet/csharp/language-reference/keywords/decimal)  
  
 詳細については、「[ビルド内にありません: グローバル属性 \(C\# プログラミング ガイド\)](http://msdn.microsoft.com/ja-jp/7c6c41f8-f0d5-4345-8987-3d91f9bae136)」を参照してください。  
  
## 使用例  
 次の例では CS0182 が生成されます。  
  
```  
// CS0182.cs public class MyClass { static string s = "Test"; [System.Diagnostics.ConditionalAttribute(s)]   // CS0182 // try the following line instead // [System.Diagnostics.ConditionalAttribute("Test")] void NonConstantArgumentToConditional() { } public static void Main() { } }  
```