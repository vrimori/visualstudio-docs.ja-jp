---
title: "コンパイラ エラー CS1935 | Microsoft Docs"
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
  - "CS1935"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1935"
ms.assetid: d5dda801-fbf3-4340-bfe1-f9409f2d344d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1935
ソース型 'type' のクエリ パターンの実装が見つかりませんでした。 'method' が見つかりません 'System.Core.dll' への参照がないか、または 'System.Linq' のディレクティブを使用していませんか ?  
  
 クエリ内のソース型は、`IEnumerable`、`IEnumerable<T>`、派生型、または自分自身または他のユーザーが標準クエリ演算子を実装した型である必要があります。 ソース型が `IEnumerable` または `IEnumerable<T>` の場合、標準クエリ演算子の拡張メソッドがスコープ内に入るようにするには、system.core.dll への参照と、System.Linq 名前空間の `using` ディレクティブを追加する必要があります。`using` ディレクティブおよび必要に応じてアセンブリへの参照を使用して、同じように標準クエリ演算子のカスタム実装をスコープ内に入るようにする必要があります。  
  
### このエラーを解決するには  
  
1.  必要な使用するディレクティブと参照をプロジェクトに追加します。  
  
## 使用例  
 System.Linq の `using` ディレクティブがコメント アウトされているため、次のコードでは CS1935 が生成されます。  
  
```  
// cs1935.cs // CS1935 using System; using System.Collections.Generic; // using System.Linq; class Test { static int Main() { int[] nums = {0,1,2,3,4,5}; IEnumerable<int> e = from n in nums where n > 3 select n; return 0; } }  
```  
  
## 参照  
 [Standard Query Operators Overview](../Topic/Standard%20Query%20Operators%20Overview.md)