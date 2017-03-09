---
title: "コンパイラ エラー CS1932 | Microsoft Docs"
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
  - "CS1932"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1932"
ms.assetid: fc927899-2d35-4d47-9ae9-8fc99295bb66
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1932
'expression' を範囲変数に割り当てることはできません。  
  
 `from` 句に導入されるか `let` 句に導入されるかにかかわらず、コンパイラは範囲変数の型を推測できなければなりません。 null は型ではないので null にすることはできません。また、安全でない型の式を割り当てることはできません。  
  
### このエラーを解決するには  
  
-   無効な割り当てを削除します。  
  
-   式を許可されている型に明示的にキャストします。  
  
## 使用例  
 次のコードでは、範囲変数の型が推測できないため、CS1932 が生成されます。 エラーを解決するには、次の例で示すように、目的の型に値をキャストします。  
  
```  
// CS1932.cs using System.Linq; class Test { static void Main() { var x = from i in Enumerable.Range(1, 100) let k = null // CS1932 // Try the following line instead. let k = (string) null select i; } }  
```  
  
## 参照  
 [LINQ クエリ式](/dotnet/csharp/programming-guide/linq-query-expressions/index)