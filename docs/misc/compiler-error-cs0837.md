---
title: "コンパイラ エラー CS0837 | Microsoft Docs"
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
  - "CS0837"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0837"
ms.assetid: cbde45dc-222c-4bfe-8814-856476319d37
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0837
演算子 'is' または 'as' の最初のオペランドを、ラムダ式または匿名メソッドにすることはできません。  
  
 ラムダ式と匿名メソッドは、[is](/dotnet/csharp/language-reference/keywords/is) または [as](/dotnet/csharp/language-reference/keywords/as) の左側に使用できません。  
  
### このエラーを解決するには  
  
-   `is` 演算子でこのエラーが発生する場合、`is` が値と型を受け取り、参照変換、ボックス化変換、またはボックス化解除変換のいずれによって値をその型に変換できるかを通知することに注意してください。 ラムダは値ではなく、参照変換、ボックス化変換、またはボックス化解除変換を行わないため、`is` の候補ではありません。  
  
-   コードで `as` が誤って使用されている場合、キャストに変更するとエラーが修正されることがあります。  
  
## 使用例  
 次の例では CS0837 が生成されます。  
  
```  
// cs0837.cs namespace TestNamespace { public delegate void Del(); class Test { static int Main() { bool b1 = (() => { }) is Del;   // CS0837 bool b2 = delegate() { } is Del;// CS0837 Del d1 = () => { } as Del;      // CS0837 Del d2 = delegate() { } as Del; // CS0837 return 1; } } }  
```