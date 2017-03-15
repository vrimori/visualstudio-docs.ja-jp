---
title: "コンパイラ エラー CS0815 | Microsoft Docs"
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
  - "CS0815"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0815"
ms.assetid: 8f055d34-9ee4-482e-9e79-8b3698c55cb4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0815
'expression' を暗黙的に型指定されたローカル変数に割り当てることはできません  
  
 暗黙的に型指定された変数の初期化子として使用される式には、型が必要です。 匿名関数式、メソッド グループ式、NULL リテラル式には型がないため、適切な初期化子ではありません。 暗黙的に型指定された変数を宣言の中で NULL 値で初期化することはできませんが、後で値 NULL を割り当てることはできます。  
  
### このエラーを解決するには  
  
1.  変数に明示的な型を指定します。  
  
## 使用例  
 次のコードでは CS0815 が生成されます。  
  
```  
// cs0815.cs class Test { public static int Main() { var d = s => -1; // CS0815 var e = (string s) => 0; // CS0815 var p = null;//CS0815 var del = delegate(string a) { return -1; };// CS0815 return -1; } }  
```  
  
## 参照  
 [暗黙的に型指定されるローカル変数](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)