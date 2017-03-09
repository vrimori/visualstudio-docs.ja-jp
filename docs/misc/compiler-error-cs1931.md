---
title: "コンパイラ エラー CS1931 | Microsoft Docs"
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
  - "CS1931"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1931"
ms.assetid: c0071c3d-ae11-4073-87df-508150daef68
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1931
範囲変数 'variable' が 'variable' の以前の宣言と競合しています。  
  
 他のすべての宣言と同様に、範囲変数の宣言には変数の宣言領域内で一意の識別子を指定する必要があります。  
  
### このエラーを解決するには  
  
1.  範囲変数に一意の名前を付けます。  
  
## 使用例  
 次のコードでは、識別子 `x` が `Main` 内でローカル変数として使用されるだけでなく、クエリ式で範囲変数としても使用されているため、CS1931 が生成されます。  
  
```  
// cs1931.cs class Test { static void Main() { int x = 1; var y = from x in Enumerable.Range(1, 100) // CS1931 select x; } }  
```  
  
## 参照  
 [LINQ クエリ式](/dotnet/csharp/programming-guide/linq-query-expressions/index)