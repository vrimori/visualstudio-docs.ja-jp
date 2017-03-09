---
title: "コンパイラ エラー CS0825 | Microsoft Docs"
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
  - "CS0825"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0825"
ms.assetid: 49393d23-ec5f-4b44-a3fd-7e0a95ac0edd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0825
コンテキスト キーワード 'var' は、ローカル変数宣言内でのみ有効です  
  
 `var` キーワードによる暗黙の型指定は、ローカル メソッド スコープの変数にのみ適用できます。  
  
### このエラーを解決するには  
  
1.  変数がクラス スコープに属している場合は、変数に明示的な型を指定します。  それ以外の場合は、使用するメソッド内に変数を移動します。  
  
## 使用例  
 次のコードでは、クラス フィールドに対して `var` を使用しているため、CS0825 が生成されます。  
  
```  
// cs0825.cs class Test { private var myField; //CS0825 static int Main() { var a = 1; // var is OK here return -1; } }  
```  
  
## 参照  
 [暗黙的に型指定されるローカル変数](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)