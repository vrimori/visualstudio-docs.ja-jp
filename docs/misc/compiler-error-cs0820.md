---
title: "コンパイラ エラー CS0820 | Microsoft Docs"
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
  - "CS0820"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0820"
ms.assetid: 38c05162-ef20-42a8-9611-02698360dec5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0820
配列初期化子を暗黙的に型指定されたローカル変数に割り当てることはできません  
  
 暗黙的に型指定される配列とは、コンパイラによって推論される要素型を持つ配列です。 コード例に示されているように、`new`\[\] 修飾子を使用して初期化する必要があります。  
  
### このエラーを解決するには  
  
-   配列初期化子と共に `new`\[\] 修飾子を使用します。  
  
-   暗黙的に型指定されたローカル変数を使用しません。  
  
## 使用例  
 次のコードでは CS0820 が生成されます。また、暗黙的に型指定される配列を正しく初期化する方法を示しています。  
  
```  
//cs0820.cs class G { public static int Main() { var a = { 1,2,3}; //CS0820 // Try using one of the following lines instead. // var b = new[] { 1, 2, 3 }; //int[] b = {1, 2, 3}; return -1; } }  
```  
  
## 参照  
 [暗黙的に型指定されるローカル変数](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)