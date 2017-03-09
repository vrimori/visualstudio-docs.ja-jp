---
title: "コンパイラ エラー CS1934 | Microsoft Docs"
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
  - "CS1934"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1934"
ms.assetid: 18624be3-d534-4695-bafd-cc664fcde15e
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1934
ソース型 'type' のクエリ パターンの実装が見つかりませんでした。 'method' が見つかりません。 範囲変数 'name' の型を明示的に指定することをご検討ください。  
  
 標準クエリ演算子が実装されていないデータ ソースがクエリ式に指定されると、このエラーが発生します。 このエラーが発生する 1 つの状況は、範囲変数に対して明示的に型を指定しないで `ArrayList` を指定することです。  
  
### このエラーを解決するには  
  
1.  次の例の場合、解決策は、単に範囲変数の型を指定することです。  
  
    ```  
    var q = from int x in list  
    ```  
  
## 使用例  
 次の例は、CS1934 が発生する 1 つの状況を示しています。  
  
```  
// cs1934.cs using System.Linq; using System.Collections; static class Test { public static void Main() { var list = new ArrayList { 0, 1, 2, 3, 4, 5 }; var q = from x in list // CS1934 select x + 1; } }  
```  
  
## 参照  
 [How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)