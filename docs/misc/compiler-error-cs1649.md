---
title: "コンパイラ エラー CS1649 | Microsoft Docs"
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
  - "CS1649"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1649"
ms.assetid: 6355c7f2-157c-441d-8925-500062988636
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1649
読み取り専用フィールド 'identifier' のメンバーに ref または out を渡すことはできません \(静的コンストラクターでは可\)。  
  
 このエラーは、関数に、`readonly` フィールドのメンバーである変数を `ref` または `out` 引数として渡した場合に発生します。`ref` および `out` パラメーターが関数によって変更される可能性があるため、これは許可されません。 このエラーを解決するには、このフィールドの `readonly` キーワードを削除するか、または `readonly` フィールドのメンバーを関数に渡さないようにします。 たとえば、次の例に示すように、変更可能な一時変数を作成して、この一時変数を `ref` 引数として渡す操作を試すことができます。  
  
## 使用例  
 次の例では CS1649 が生成されます。  
  
```  
// CS1649.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { Outer outer = new Outer(); f(ref outer.inner.i);  // CS1649 // Try this code instead: // int tmp = outer.inner.i; // f(ref tmp); } }  
```