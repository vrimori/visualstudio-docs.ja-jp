---
title: "コンパイラ エラー CS1655 | Microsoft Docs"
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
  - "CS1655"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1655"
ms.assetid: 041e9daa-c026-494f-b086-0db9a23c969b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1655
'variable' は 'readonly variable type' であるため、フィールドを ref または out 引数として渡すことはできません。  
  
 このエラーは、[foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 変数、[using](/dotnet/csharp/language-reference/keywords/using-statement) 変数、または [fixed](/dotnet/csharp/language-reference/keywords/fixed-statement) 変数のメンバーを ref または out 引数として関数に渡そうとすると発生します。 これらのコンテキストにおいて、これらの変数は読み取り専用と見なされるため、このような操作は許可されません。  
  
 次の例では CS1655 が生成されます。  
  
```  
// CS1655.cs struct S { public int i; } class CMain { static void f(ref int iref) { } public static void Main() { S[] sa = new S[10]; foreach(S s in sa) { CMain.f(ref s.i);  // CS1655 } } }  
```