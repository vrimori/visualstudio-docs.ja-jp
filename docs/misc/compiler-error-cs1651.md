---
title: "コンパイラ エラー CS1651 | Microsoft Docs"
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
  - "CS1651"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1651"
ms.assetid: ce1043e3-b453-4b4c-b949-f344834e3845
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1651
静的読み取り専用フィールド 'identifier' には、静的コンストラクター内を除き、ref または out を渡すことはできません。  
  
 このエラーは、関数に、静的読み取り専用フィールドのメンバーである変数を ref 引数として渡した場合に発生します。 ref パラメーターが関数によって変更される可能性があるため、これは許可されません。 このエラーを解決するには、このフィールドの **readonly** キーワードを削除するか、または読み取り専用フィールドのメンバーを関数に渡さないようにします。 たとえば、次の例に示すように、変更可能な一時変数を作成して、この一時変数を ref 引数として渡す操作を試すことができます。  
  
 次の例では CS1651 が生成されます。  
  
```  
// CS1651.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { f(ref Outer.inner.i);  // CS1651 // Try this instead: // int tmp = Outer.inner.i; // f(ref tmp); } }  
```