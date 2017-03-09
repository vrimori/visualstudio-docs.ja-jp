---
title: "コンパイラ エラー CS1100 | Microsoft Docs"
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
  - "CS1100"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1100"
ms.assetid: ea233371-36b6-49ae-a98c-a00ee3b79e53
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1100
メソッド 'name' には、最初のパラメーター以外でパラメーター修飾子 'this' が指定されています。  
  
 `this` 修飾子は、メソッドが拡張メソッドであることをコンパイラに通知する、メソッドの最初のパラメーターに対してのみ指定できます。  
  
### このエラーを解決するには  
  
1.  メソッドの最初のパラメーターを除くすべてのパラメーターから `this` 修飾子を削除します。  
  
## 使用例  
 次のコードでは、`this`  パラメーターが 2 番目のパラメーターを変更するため、CS1100 が生成されます。  
  
```  
// cs1100.cs static class Test { static void ExtMethod(int i, this Test c) // CS1100 { } }  
```  
  
## 参照  
 [拡張メソッド](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)