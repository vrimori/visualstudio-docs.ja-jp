---
title: "コンパイラ エラー CS0564 | Microsoft Docs"
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
  - "CS0564"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0564"
ms.assetid: 4c152e10-eb22-4437-a85f-1599c76470e0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0564
オーバーロードされた shift 演算子の最初のオペランドはそれを含む型と同じ型、2 番目のオペランドの型は int でなければなりません  
  
 入力したオペランドに誤りがあるシフト演算子 \(\<\< または \>\>\) をオーバーロードしようとしました。 最初のオペランドはその型で、2 番目のオペランドは型 `int` である必要があります。  
  
 次の例では CS0564 が生成されます。  
  
```  
// CS0564.cs using System; class C { public static int operator << (C c1, C c2) // CS0564 // To correct, change second operand to int, like so: // public static int operator << (C c1, int c2) { return 0; } static void Main() { } }  
```