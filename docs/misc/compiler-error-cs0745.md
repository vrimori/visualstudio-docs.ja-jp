---
title: "コンパイラ エラー CS0745 | Microsoft Docs"
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
  - "CS0745"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0745"
ms.assetid: 6ae77eb2-a940-43aa-a198-3042d144613a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0745
コンテキスト キーワード 'by' が必要です。  
  
 `group` 句のパターンは、次の例に示すように、`group...by` の後に続けて省略可能な `into` が続きます。  
  
```  
string[] names = { "Bob", "Bill", "Jonetta", "Mary" }; var query = from name in names group name by name[0];  
```  
  
 、または  
  
```  
var query2 = from name in names group name by name[0] into g //...additional query clauses  
```  
  
### このエラーを解決するには  
  
1.  `by` キーワードを `group` 句に追加します。  
  
## 使用例  
 次のコードでは CS0745 が生成されます。  
  
```  
// cs0745.cs using System; using System.Linq; public class C { public static int Main() { string[] names = { "Bob", "Bill", "Jonetta", "Mary" }; var query = from name in names group name name[0]; // CS0745 return 1; } }  
```  
  
## 参照  
 [LINQ クエリ式](/dotnet/csharp/programming-guide/linq-query-expressions/index)   
 [group 句](/dotnet/csharp/language-reference/keywords/group-clause)