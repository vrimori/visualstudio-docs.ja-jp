---
title: "コンパイラ エラー CS0594 | Microsoft Docs"
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
  - "CS0594"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0594"
ms.assetid: a3d6bde1-db63-4c5c-a425-8c6a39e00999
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0594
浮動小数点定数が型 'type' の範囲外です  
  
 値が、このデータ型の変数に対して大きすぎる浮動小数点変数に割り当てられました。 データ型で使用できる値の範囲については、[整数型の一覧表](/dotnet/csharp/language-reference/keywords/integral-types-table)を参照してください。  
  
 次の例では CS0594 が生成されます。  
  
```  
// CS0594.cs namespace MyNamespace { public class MyClass { public static void Main() { float f = 6.77777777777E400;   // CS0594, value too large } } }  
```