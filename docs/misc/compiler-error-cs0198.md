---
title: "コンパイラ エラー CS0198 | Microsoft Docs"
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
  - "CS0198"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0198"
ms.assetid: 222c20f6-3f7f-4750-9f99-b5e6ae6c1271
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0198
静的読み取り専用フィールド 'name' のフィールドへの割り当てはできません \(静的コンストラクターまたは変数初期化子では可\)  
  
 [readonly](/dotnet/csharp/language-reference/keywords/readonly) 変数は、それを初期化するコンストラクターと同じように [static](/dotnet/csharp/language-reference/keywords/static) を使用する必要があります。 詳細については、「[静的コンストラクター](/dotnet/csharp/programming-guide/classes-and-structs/static-constructors)」を参照してください。  
  
 次の例では CS0198 が生成されます。  
  
```  
// CS0198.cs class MyClass { public static readonly int TestInt = 6; MyClass() { TestInt = 11;   // CS0198, constructor is not static and readonly field is } public static void Main() { } }  
```