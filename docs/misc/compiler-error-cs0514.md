---
title: "コンパイラ エラー CS0514 | Microsoft Docs"
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
  - "CS0514"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0514"
ms.assetid: 74ce3010-f9e9-458c-8b68-cfb908a3e7a2
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0514
'constructor' : 静的コンストラクターには、明示的な 'this' または 'base' コンストラクターの呼び出しを含めることはできません  
  
 静的コンストラクターでの `this` の呼び出しは、静的コンストラクターが、クラスのインスタンスを作成する前に自動的に呼び出されるため、使用できません。 また、静的コンストラクターは継承されず、直接呼び出すこともできません。  
  
 詳細については、[this](/dotnet/csharp/language-reference/keywords/this) および [base](/dotnet/csharp/language-reference/keywords/base) を参照してください。  
  
## 使用例  
 次の例では CS0514 が生成されます。  
  
```  
// CS0514.cs class A { static A() : base(0) // CS0514 { } public A(object o) { } } class B { static B() : this(null) // CS0514 { } public B(object o) { } }  
```