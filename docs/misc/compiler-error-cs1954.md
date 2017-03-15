---
title: "コンパイラ エラー CS1954 | Microsoft Docs"
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
  - "CS1954"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1954"
ms.assetid: bdec399e-c43d-46d3-a01b-ef3572786fe5
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1954
コレクション初期化子要素に最も適しているオーバーロード メソッド 'method' は使用できません。 コレクション初期化子 'Add' メソッドには、ref または out パラメーターを指定できません。  
  
 コレクション初期化子を使用してコレクション クラスを初期化するには、このクラスに `ref` パラメーターでも `out` パラメーターでもない `public` `Add` メソッドを指定する必要があります。  
  
### このエラーを解決するには  
  
-   コレクション クラスのソース コードを変更できる場合は、`ref` パラメーターも `out` パラメーターも持たない `Add` メソッドを指定します。  
  
-   コレクション クラスを変更できない場合は、コレクション クラスが指定するコンストラクターでコレクション クラスを初期化します。 コレクション初期化子を使用することはできません。  
  
## 使用例  
 次の例では、`MyList` の `Add` リストの中で利用できる唯一のオーバーロードが `ref` パラメーターを持っているため、CS1954 が生成されます。  
  
```  
// cs1954.cs using System.Collections.Generic; class MyList<T> : IEnumerable<T> { List<T> _list; public void Add(ref T item) { _list.Add(item); } public System.Collections.Generic.IEnumerator<T> GetEnumerator() { int index = 0; T current = _list[index]; while (current != null) { yield return _list[index++]; } } System.Collections.IEnumerator System.Collections.IEnumerable.GetEnumerator() { return GetEnumerator(); } } public class MyClass { public string tree { get; set; } } class Program { static void Main(string[] args) { MyList<MyClass> myList = new MyList<MyClass> { new MyClass { tree = "maple" } }; // CS1954 } }  
  
```  
  
## 参照  
 [オブジェクト初期化子とコレクション初期化子](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)