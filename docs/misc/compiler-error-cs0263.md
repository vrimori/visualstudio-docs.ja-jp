---
title: "コンパイラ エラー CS0263 | Microsoft Docs"
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
  - "CS0263"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0263"
ms.assetid: 94fe3eb0-10e9-4602-a993-68fe125c8565
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0263
'type' の部分宣言では、異なる基底クラスを指定できません  
  
 部分宣言で型を定義する場合は、各部分の宣言で同じ基本型を指定します。 詳細については、「[部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)」を参照してください。  
  
 次の例では CS0263 が生成されます。  
  
```  
  
// CS0263.cs // compile with: /target:library class B1 { } class B2 { } partial class C : B1  // CS0263 – is the base class B1 or B2? { } partial class C : B2 { }  
```