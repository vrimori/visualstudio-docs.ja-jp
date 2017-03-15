---
title: "コンパイラの警告 (レベル 1) CS0197 | Microsoft Docs"
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
  - "CS0197"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0197"
ms.assetid: 2b5b1b8d-ce13-4bd7-b80a-abb80e9f79ad
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS0197
参照マーシャリング クラスのフィールドであるため、'argument' を ref または out として渡す、またはそのアドレスを取得すると、ランタイム例外が発生する可能性があります  
  
 <xref:System.MarshalByRefObject> から直接的または間接的に派生したクラスは、参照渡しのマーシャリング クラスです。 このようなクラスは、プロセスやコンピューターの境界を越えて、参照によってマーシャリングできます。 したがって、このクラスのインスタンスは、リモート オブジェクトに対するプロキシである可能性があります。 プロキシ オブジェクトのフィールドを [ref](/dotnet/csharp/language-reference/keywords/ref) または [out](/dotnet/csharp/language-reference/keywords/out) として渡すことはできません。 そのため、インスタンスがプロキシ オブジェクトにはできない [this](/dotnet/csharp/language-reference/keywords/this) でない限り、このようなクラスのフィールドを `ref` または `out` として渡すことはできません。  
  
## 使用例  
 次の例では CS0197 が生成されます。  
  
```  
// CS0197.cs // compile with: /W:1 class X : System.MarshalByRefObject { public int i; } class M { public int i; static void AddSeventeen(ref int i) { i += 17; } static void Main() { X x = new X(); x.i = 12; AddSeventeen(ref x.i);   // CS0197 // OK M m = new M(); m.i = 12; AddSeventeen(ref m.i); } }  
```