---
title: "コンパイラ エラー CS1940 | Microsoft Docs"
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
  - "CS1940"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1940"
ms.assetid: 546e9bba-725d-4ea9-826f-37ec9d832add
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1940
ソース型 'type' に対してクエリ パターンの複数の実装が見つかりました。 'method' の呼び出しがあいまいです。  
  
 このエラーは、クエリ メソッドの実装が複数定義されていて、クエリに使用する最適な実装をコンパイラが判断できない場合に発生します。 次の例では、`Select` の両方のバージョンが入力パラメーターとして `int` を受け取り、戻り値として `int` を使用するため、両方とも同じシグネチャを使用することになります。  
  
### このエラーを解決するには  
  
1.  メソッドごとに 1 つの実装のみ用意します。  
  
## 使用例  
 次のコードでは CS1940 が生成されます。  
  
```  
// cs1940.cs using System; //must include explicitly for types defined in 3.5 class Test { public delegate int Dele(int x); int num = 0; public int Select(Func<int, int> d) { return d(this.num); } public int Select(Dele d) // CS1940 { return d(this.num) + 1; } public static void Main() { var q = from x in new Test() select x; } }  
```  
  
## 参照  
 [Standard Query Operators Overview](../Topic/Standard%20Query%20Operators%20Overview.md)