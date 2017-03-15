---
title: "コンパイラ エラー CS0751 | Microsoft Docs"
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
  - "CS0751"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0751"
ms.assetid: 2ebaed5f-d3ca-452f-8fce-f3299b84360a
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0751
部分メソッドは、部分クラスまたは部分構造体内で宣言される必要があります  
  
 部分クラスまたは部分構造体内にカプセル化しない限り、[partial](/dotnet/csharp/language-reference/keywords/partial-method) メソッドを宣言することはできません。  
  
### このエラーを解決するには  
  
1.  メソッドから `partial` 修飾子を削除し実装を提供するか、`partial` 修飾子を外側のクラスまたは構造体に追加します。  
  
## 使用例  
 次の例では CS0751 が生成されます。  
  
```  
// cs0751.cs using System; public class C { partial void Part(); // CS0751 public static int Main() { return 1; } }  
```  
  
## 参照  
 [部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)