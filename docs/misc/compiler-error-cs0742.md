---
title: "コンパイラ エラー CS0742 | Microsoft Docs"
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
  - "CS0742"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0742"
ms.assetid: 078ee7af-17e4-4572-8fee-d97e09c9002b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0742
クエリ本体の後には select 句または group 句が必要です  
  
 クエリ式は、継続なしで `select` 句または `group` 句のいずれかで終了する必要があります。  
  
### このエラーを解決するには  
  
1.  クエリに [select 句](/dotnet/csharp/language-reference/keywords/select-clause)または [group 句](/dotnet/csharp/language-reference/keywords/group-clause)を追加します。  
  
## 使用例  
 次のコードでは CS0742 が生成されます。  
  
```  
// cs0742.cs using System.Linq; public class Test { public static int Main() { int[] array = { 1, 2, 3 }; var query = from num in array; // CS0742 return 1; } }  
```  
  
 `group` 句で [into](/dotnet/csharp/language-reference/keywords/into) キーワードを使用して、一時識別子にグループ化の結果を格納する場合は、この句をクエリの最後の句にすることはできません。`select` 句または 2 番目の `group` 句が必要です。  
  
## 参照  
 [LINQ クエリ式](/dotnet/csharp/programming-guide/linq-query-expressions/index)