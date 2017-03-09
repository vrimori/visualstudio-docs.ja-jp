---
title: "コンパイラ エラー CS0131 | Microsoft Docs"
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
  - "CS0131"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0131"
ms.assetid: 822852cc-a426-4b7d-b2ff-0026a0c0a0e7
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0131
代入式の左辺には変数、プロパティ、またはインデクサーを指定してください。  
  
 代入ステートメントでは、右辺の値が左辺に代入されます。 左辺には、変数、プロパティ、またはインデクサーのいずれかを指定してください。  
  
 このエラーを解決するには、すべての演算子が右辺にあり、左辺が変数、プロパティ、またはインデクサーのいずれかであることを確認します。 詳細については、「[ステートメント、式、および演算子](/dotnet/csharp/programming-guide/statements-expressions-operators/index)」を参照してください。  
  
## 使用例  
 次の例では CS0131 が生成されます。  
  
```  
// CS0131.cs public class MyClass { public int i = 0; public void MyMethod() { i++ = 1;   // CS0131 // try the following line instead // i = 1; } public static void Main() { } }  
```  
  
## 使用例  
 このエラーは、代入演算子の左辺で、次のような算術演算を実行しようとした場合にも発生します。  
  
```  
// CS0131b.cs public class C { public static int Main() { int a = 1, b = 2, c = 3; if (a + b = c) // CS0131 // try this instead // if (a + b == c) return 0; return 1; } }  
```