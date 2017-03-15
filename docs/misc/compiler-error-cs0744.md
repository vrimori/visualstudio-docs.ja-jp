---
title: "コンパイラ エラー CS0744 | Microsoft Docs"
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
  - "CS0744"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0744"
ms.assetid: 7ce430d6-737a-4103-9116-d9a4a69f8af3
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0744
コンテキスト キーワード 'equals' が必要です。  
  
 `join` 句のパターンは、この例のように、`join`...`in`...`on`...`equals` です。  
  
```  
var query = from x in array1 join y in array2 on x equals y select x;  
```  
  
### このエラーを解決するには  
  
1.  `equals` キーワードを `join` 句に追加します。  
  
## 使用例  
 次のコードでは CS0744 が生成されます。  
  
```  
// cs0744.cs using System; using System.Linq; public class C { public static int Main() { int[] array1 = { 1, 2, 3 ,4, 5, 6,}; int[] array2 = { 5, 6, 7, 8, 9 }; var c = from x in array1 join y in array2 on x y // CS0744 select x; return 1; } }  
```  
  
## 参照  
 [LINQ クエリ式](/dotnet/csharp/programming-guide/linq-query-expressions/index)   
 [join 句](/dotnet/csharp/language-reference/keywords/join-clause)