---
title: "コンパイラ エラー CS0838 | Microsoft Docs"
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
  - "CS0838"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0838"
ms.assetid: 22495e47-3331-42ef-921c-f76ff03ef1f7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0838
式ツリーに多次元配列初期化子を含めることはできません。  
  
 配列初期化子を使用して式ツリー内の多次元配列を初期化できません。  
  
### このエラーを解決するには  
  
1.  式ツリーを作成する前に、配列を作成および初期化します。  
  
## 使用例  
 次の例では CS0838 が生成されます。  
  
```  
// cs0838.cs using System; using System.Linq; using System.Linq.Expressions; namespace TestNamespace { class Test { static int Main() { Expression<Func<int[,]>> expr = () => new int[2, 2] { { 1, 2 }, { 3, 4 } }; // CS0838 // try the following 2 lines instead int[,] nums = new int[2, 2] { { 1, 2 }, { 3, 4 } }; Expression<Func<int[,]>> expr2 = () => nums; return 1; } } }  
  
```  
  
## 参照  
 [式ツリー](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)