---
title: "コンパイラ エラー CS1922 | Microsoft Docs"
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
  - "CS1922"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1922"
ms.assetid: a4098a25-6581-4966-b61d-318cd12f76d3
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1922
コレクション初期化子では、System.Collections.IEnumerable の実装にその型 'type' が必要です。  
  
 型を指定してコレクション初期化子を使用するには、この型に `IEnumerable` を実装する必要があります。 このエラーは、オブジェクト初期化子を使用するときに誤ってコレクション初期化子構文を使用した場合に発生する可能性があります。  
  
### このエラーを解決するには  
  
-   この型がコレクションを表していない場合は、コレクション初期化子構文ではなくオブジェクト初期化子構文を使用します。  
  
-   この型がコレクションを表している場合は、コレクション初期化子を使用してその型のオブジェクトを初期化する前に、型を変更して `IEnumerable` を実装します。  
  
-   この型がコレクションを表し、ソース コードへのアクセス権がない場合は、クラス コンストラクターまたは他の初期化メソッドを使用してその要素を初期化します。  
  
## 使用例  
 次のコードでは CS1922 が生成されます。  
  
```  
// cs1922.cs public class Test { public static void Main() { // Collection initializer. var tc = new TestClass  {1,"hello"} ; // CS1922 // Object initalizer. var tc2 = new TestClass { memberA = 1, memberB = "hello" }; // OK } } public class TestClass { public int memberA { get; set; } public string memberB { get; set; } }  
  
```  
  
## 参照  
 [オブジェクト初期化子とコレクション初期化子](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)