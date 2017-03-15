---
title: "&#39;&lt;typename&gt;&#39; はデリゲート型ではないため、ラムダ式を &#39;&lt;typename&gt;&#39; に変換できません。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36625"
  - "vbc36625"
helpviewer_keywords: 
  - "BC36625"
ms.assetid: c03634d4-d831-4f8c-b6ab-566465968e4d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; はデリゲート型ではないため、ラムダ式を &#39;&lt;typename&gt;&#39; に変換できません。
ラムダ式は、デリゲートが使用できる場所で使用できます。 ラムダ式は互換性のあるデリゲート型には変換できますが、その他の型には変換できません。 たとえば、デリゲート型を定義してこれにラムダ式を割り当てることや、ラムダ式を <xref:System.Func%601> パラメーターへの引数として送信することができます。 次のコードに例を示します。  
  
```vb#  
Module Module1 Delegate Function FunDel(ByVal m As Integer) As Boolean Sub Main() ' Assign a lambda expression to a function delegate. Dim negative As FunDel = Function(n As Integer) n < 0 Console.WriteLine(negative(-3)) ' Send a lambda as the argument to a delegate parameter. Dim numbers() As Integer = {3, 4, 2, 8, 1, 0, 9, 13, 42} Dim evens = numbers.Where(Function(n) n Mod 2 = 0) For Each even In evens Console.WriteLine(even) Next End Sub End Module  
```  
  
 **エラー ID:** BC36625  
  
## 参照  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)