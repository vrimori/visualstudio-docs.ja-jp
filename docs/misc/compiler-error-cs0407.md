---
title: "コンパイラ エラー CS0407 | Microsoft Docs"
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
  - "CS0407"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0407"
ms.assetid: 59112fb9-4641-466e-b738-b3228539a09e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0407
'return\-type method' には、正しくない戻り値の型が指定されています  
  
 メソッドとデリゲート型との間に互換性がありませんでした。 引数の型は一致しましたが、戻り値の型は、そのデリゲートの正しい戻り値の型ではありませんでした。 このエラーを回避するには、別のメソッドを使用するか、メソッドの戻り値の型を変更するか、デリゲートの戻り値の型を変更します。  
  
## 使用例  
 次の例では CS0407 が生成されます。  
  
```  
// CS0407.cs public delegate int MyDelegate(); class C { MyDelegate d; public C() { d = new MyDelegate(F);  // OK: F returns int d = new MyDelegate(G);  // CS0407 – G doesn't return int } public int F() { return 1; } public void G() { } public static void Main() { C c1 = new C(); } }  
```