---
title: "コンパイラ エラー CS0214 | Microsoft Docs"
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
  - "CS0214"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0214"
ms.assetid: be1ef909-a53e-485f-a79b-b1cc56cead15
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0214
ポインターおよび固定サイズ バッファーは、unsafe コンテキストでのみ使用することができます。  
  
 ポインターは [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) キーワードとのみ使用できます。 詳細については、「[unsafe コードとポインター](/dotnet/csharp/programming-guide/unsafe-code-pointers/index)」を参照してください。  
  
 次の例では CS0214 が生成されます。  
  
```  
// CS0214.cs // compile with: /target:library /unsafe public struct S { public int a; } public class MyClass { public static void Test() { S s = new S(); S * s2 = &s;    // CS0214 s2->a = 3;      // CS0214 s.a = 0; } // OK unsafe public static void Test2() { S s = new S(); S * s2 = &s; s2->a = 3; s.a = 0; } }  
```