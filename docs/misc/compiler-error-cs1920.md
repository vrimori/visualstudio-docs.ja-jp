---
title: "コンパイラ エラー CS1920 | Microsoft Docs"
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
  - "CS1920"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1920"
ms.assetid: efb4782f-a222-4fb5-9e79-8bd2d380520b
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1920
要素の初期化子を空白にはできません。  
  
 コレクション初期化子は、連続する要素の初期化子で構成されます。 要素の初期化子に代入式が含まれていない場合、それをかっこで囲む必要はありません。 ただし、かっこで囲む場合は、それを空白にできません。 要素の初期化子がオブジェクト初期化子の場合は、初期化子に新しいオブジェクトの作成式が含まれている場合に限り、かっこを空白にできます。  
  
### このエラーを解決するには  
  
-   見つからない式をかっこ内に追加します。  
  
-   式をオブジェクト初期化子にする場合は、新しいオブジェクトの作成式をかっこの前に追加します。  
  
## 使用例  
 次の例では CS1920 が生成されます。  
  
```  
// cs1920.cs using System.Collections.Generic; public class Test { public static int Main() { // Error. Empty initializer // for inner list. List<List<int>> collection = new List<List<int>>() { { } }; // CS1920 // OK. No initializer for inner list. List<List<int>> collection2 = new List<List<int>>() {  }; // OK. Inner list is initialized // to one List<int> with zero elements. List<List<int>> collection3 = new List<List<int>>() { new List<int> { } }; return 0; } }  
```  
  
## 参照  
 [オブジェクト初期化子とコレクション初期化子](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)