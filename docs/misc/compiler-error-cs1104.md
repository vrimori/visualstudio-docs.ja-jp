---
title: "コンパイラ エラー CS1104 | Microsoft Docs"
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
  - "CS1104"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1104"
ms.assetid: 65bfe85f-8dd1-4aed-bcd1-1f7e0635868c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1104
パラメーター配列は、拡張メソッドで 'this' 修飾子と共に使用することはできません。  
  
 拡張メソッドの最初のパラメーターを params 配列にすることはできません。  
  
### このエラーを解決するには  
  
1.  拡張メソッド定義の最初のパラメーターでは、そのメソッドが "拡張" する型を指定することに注意してください。 これは、入力パラメーターではありません。 そのため、この場所に params 配列を指定しても意味がありません。 params 配列を渡す必要がある場合は、それを 2 番目のパラメーターにします。  
  
## 使用例  
 次の例では、CS1104 が生成されます。  
  
```  
// cs1104.cs // Compile with: /target:library public static class Extensions { public static void Test<T>(this params T[] tArr) {} // CS1104 }   
```  
  
## 参照  
 [拡張メソッド](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [params](/dotnet/csharp/language-reference/keywords/params)