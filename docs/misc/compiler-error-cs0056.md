---
title: "コンパイラ エラー CS0056 | Microsoft Docs"
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
  - "CS0056"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0056"
ms.assetid: 8878b09c-5b7b-40e0-be0d-61ef5b36c151
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0056
アクセシビリティに一貫性がありません。戻り値の型 'type' のアクセシビリティは演算子 'operator' よりも低く設定されています  
  
 パブリック コンストラクトは、パブリックにアクセスできるオブジェクトを返す必要があります。 詳細については、「[アクセス修飾子](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)」を参照してください。  
  
 次の例では CS0056 が生成されます。  
  
```  
// CS0056.cs class MyClass // try the following line instead // public class MyClass { } public class A { public static implicit operator MyClass(A a)   // CS0056 { return new MyClass(); } public static void Main() { } }  
```