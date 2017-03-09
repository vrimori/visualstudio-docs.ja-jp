---
title: "コンパイラ エラー CS1930 | Microsoft Docs"
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
  - "CS1930"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1930"
ms.assetid: d28d2334-825c-4ffc-b9e9-f5d61f44d672
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1930
範囲変数 'name' は既に宣言されています。  
  
 クエリ式が終了するまで、クエリ式の範囲変数がスコープ内に存在します。 そのため、一意の識別子が必要です。  
  
### このエラーを解決するには  
  
1.  クエリ式で導入された各範囲変数に、一意の名前を指定します。  
  
## 使用例  
 次の例では、識別子 `num` が、`from` 句の範囲変数および `let` 句によって導入された範囲変数に使用されるため、CS1930 が生成されます。  
  
```  
// cs1930.cs using System.Linq; class Program { static void Main() { int[] nums = { 0, 1, 2, 3, 4, 5 }; var query = from num in nums let num = 3 // CS1930 select num; } }  
```  
  
## 参照  
 [LINQ クエリ式](/dotnet/csharp/programming-guide/linq-query-expressions/index)