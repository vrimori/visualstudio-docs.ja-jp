---
title: "コンパイラ エラー CS0460 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0460"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0460"
ms.assetid: 98d39ded-d3f9-4520-b912-892e574c056b
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0460
オーバーライドおよび明示的なインターフェイスの実装メソッドの制約は、基本メソッドから継承されるので、直接指定できません  
  
 派生クラスの一部であるジェネリック メソッドが基底クラスのメソッドをオーバーライドする場合、オーバーライドされるメソッドに制約を指定することはできません。 派生クラスのオーバーライドする側のメソッドは、基底クラスのメソッドからその制約を継承します。  
  
## 使用例  
 次の例では CS0460 が生成されます。  
  
```  
// CS0460.cs // compile with: /target:library class BaseClass { BaseClass() { } } interface I { void F1<T>() where T : BaseClass; void F2<T>() where T : struct; void F3<T>() where T : BaseClass; } class ExpImpl : I { void I.F1<T>() where T : BaseClass {}   // CS0460 void I.F2<T>() where T : class {}  // CS0460 }  
```