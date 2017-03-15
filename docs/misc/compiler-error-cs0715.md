---
title: "コンパイラ エラー CS0715 | Microsoft Docs"
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
  - "CS0715"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0715"
ms.assetid: e3cd1e46-ccfa-4678-a2ed-69245f3558ba
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0715
'static class' : 静的クラスに、ユーザー定義された演算子を含めることはできません  
  
 ユーザー定義の演算子は、クラスのインスタンスに対して作用します。 静的クラスをインスタンス化することはできないため、演算子が作用するインスタンスを作成できません。 そのため、ユーザー定義の演算子は、静的クラスでは使用できません。  
  
 次の例では CS0715 が生成されます。  
  
```  
// CS0715.cs public static class C { public static C operator+(C c)  // CS0715 { } public static void Main() { } }  
```