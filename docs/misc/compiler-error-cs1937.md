---
title: "コンパイラ エラー CS1937 | Microsoft Docs"
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
  - "CS1937"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1937"
ms.assetid: f13e8dc9-8c20-477e-8b74-7192848e08a2
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1937
名前 'name' は、'equals' の左側のスコープにありません。 'equals' のいずれかの側の式の交換を検討してください。  
  
 `equals` キーワードは、2 つの式が等しいかどうかを判断するために `join` 句で使用される特別な演算子です。 左側のソース シーケンスの範囲変数は等式の左側のスコープ内にあり、右側のソースの範囲変数は等式の左側のスコープ内のみにあります。 これは、次のコード例で IntelliSense を使用して試すことにより確認できます。  
  
### このエラーを解決するには  
  
1.  次の例のコメント行に示すように、2 つの範囲変数の位置を交換します。  
  
## 使用例  
 次の例では、CS1937 が生成されます。  
  
```  
// cs1937.cs using System.Linq; class Test { static void Main() { int[] sourceA = { 1, 2, 3, 4, 5 }; int[] sourceB = { 3, 4, 5, 6, 7 }; var query = from a in sourceA join b in sourceB on b equals a // CS1937 // Try the following line instead. //join b in sourceB on a equals b select new { a, b }; } }  
```  
  
 左側は通常、「外部」と呼ばれ、右側は通常、「内部」と呼ばれます。  
  
## 参照  
 [join 句](/dotnet/csharp/language-reference/keywords/join-clause)