---
title: "コンパイラ エラー CS1945 | Microsoft Docs"
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
  - "CS1945"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1945"
ms.assetid: 787f61b0-4767-451c-8c78-8e456b5057eb
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1945
式ツリーに匿名メソッド式を含めることはできません。  
  
 式ツリーには、式のみを含めることができます。 匿名メソッドは、ステートメントのみを表すことができます。  
  
### このエラーを解決するには  
  
1.  ステートメントを使用して式ツリーを作成しないでください。  
  
## 使用例  
 次のコードでは CS1945 が生成されます。  
  
```  
// cs1945.cs using System; using System.Linq.Expressions; public delegate void D(); class Test { static void Main() { Expression<Func<int, Func<int, bool>>> tree = (x => delegate(int i) { return true; }); // CS1945 } }  
```  
  
## 参照  
 [式ツリー](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)   
 [ステートメント、式、および演算子](/dotnet/csharp/programming-guide/statements-expressions-operators/index)