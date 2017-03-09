---
title: "コンパイラ エラー CS1950 | Microsoft Docs"
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
  - "CS1950"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1950"
ms.assetid: e37fb5b1-09e0-47a6-9db5-a48f90ea7bbb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1950
コレクション初期化子に最も適しているオーバーロード Add メソッド 'name' には無効な引数がいくつか含まれています  
  
 コレクション初期化子をサポートするには、クラスで IEnumerable を実装し、パブリック `Add` メソッドが必要です。 コレクション初期化子を使用して型を初期化するには、`Add` メソッドの入力パラメーターが、追加しようとしているオブジェクトの型と互換性がなければなりません。  
  
### このエラーを解決するには  
  
-   コレクション初期化子で互換性のある型を使用します。  
  
-   コレクション型の `Add` メソッドの入力パラメーターまたはアクセシビリティ \(あるいはその両方\) を変更します。  
  
-   渡そうとしている内容に対応する入力パラメーターを指定して、新しい `Add` メソッドを追加します。  
  
-   コレクション クラスをジェネリックにして、どの型を渡しても受け入れる `Add` メソッドを持てるようにします。  
  
## 使用例  
 次の例では、CS1950 が生成されます。  
  
```  
// cs1950.cs using System.Collections; class TestClass : CollectionBase { public void Add(int c) { } } class Test { static void Main() { TestClass t = new TestClass { "hi" }; // CS1950 } }  
```  
  
## 参照  
 [オブジェクト初期化子とコレクション初期化子](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)