---
title: "コンパイラ エラー CS0239 | Microsoft Docs"
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
  - "CS0239"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0239"
ms.assetid: 2e07bbc2-03a9-44b2-b321-477ca95fff8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0239
'member' : 継承されたメンバー 'inherited member' はシールされているため、オーバーライドできません。  
  
 メンバーは、[シール](/dotnet/csharp/language-reference/keywords/sealed)されている継承されたメンバーを[オーバーライド](/dotnet/csharp/language-reference/keywords/override)することはできません。 詳細については、「[Checked と Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)」を参照してください。  
  
 次の例では CS0239 が生成されます。  
  
```  
// CS0239.cs abstract class MyClass { public abstract void f(); } class MyClass2 : MyClass { public static void Main() { } public override sealed void f() { } } class MyClass3 : MyClass2 { public override void f()   // CS0239 // Try the following definition instead: // public new void f() { } }  
```