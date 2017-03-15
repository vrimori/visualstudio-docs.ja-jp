---
title: "コンパイラ エラー CS1947 | Microsoft Docs"
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
  - "CS1947"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1947"
ms.assetid: e2822fba-a176-4466-9cdc-63c44e22ebcb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1947
範囲変数 'variable name' が割り当てられません \-\- 読み取り専用です。  
  
 範囲変数は `foreach` ステートメントの反復変数に似ています。 これをクエリ式に割り当てることはできません。  
  
### このエラーを解決するには  
  
1.  範囲変数への割り当てを削除します。  
  
2.  必要に応じて、`let` 句を使用して新しい範囲変数を導入し、この変数を使用して値を格納します。  
  
## 使用例  
 次のコードでは CS1947 が生成されます。  
  
```  
// cs1947.cs using System.Linq; class Test { static void Main() { int[] array = new int[] { 1, 2, 3, 4, 5 }; var x = from i in array let k = i select i = 5; // CS1947 x.ToList(); } }  
```  
  
## 参照  
 [LINQ クエリ式](/dotnet/csharp/programming-guide/linq-query-expressions/index)