---
title: "コンパイラ エラー CS1955 | Microsoft Docs"
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
  - "CS1955"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1955"
ms.assetid: 38a8542d-da53-4739-b807-46c8c077363c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1955
実行不可能なメンバー 'name' をメソッドのように使用することはできません。  
  
 メソッドとデリゲートだけを呼び出すことができます。 このエラーは、空のかっこを使用してメソッドまたはデリゲート以外のものを呼び出そうとすると生成されます。  
  
### このエラーを解決するには  
  
1.  式からかっこを削除します。  
  
## 使用例  
 次のコードはメソッド呼び出し演算子 [\(\)](/dotnet/csharp/language-reference/operators/invocation-operator) を使用してフィールドとプロパティを呼び出そうとしているため、CS1955 が生成されます。 フィールドまたはプロパティを呼び出すことはできませんが、メンバー アクセス演算子 \( [.](/dotnet/csharp/language-reference/operators/member-access-operator) \) を使用して、格納される値にアクセスすることができます。  
  
```  
// cs1955.cs class A { public int x = 0; public int X { get { return x; } set { x = value; } } } class Test { static int Main() { A a = new A(); a.x(); // CS1955 a.X(); // CS1955 // Try this line instead: // int num = a.x; } }  
```