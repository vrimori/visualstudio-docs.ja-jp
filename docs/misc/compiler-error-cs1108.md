---
title: "コンパイラ エラー CS1108 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1108"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1108"
ms.assetid: 26e82d6a-6ebf-4beb-912e-1bcb86b668aa
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1108
パラメーターに、指定したすべての修飾子を設定することはできません。パラメーターに含まれる修飾子が多すぎます。  
  
 `ref` と `out` などの特定のパラメーター修飾子の組み合わせは、コンパイラに対して相反する意味があるために使用できません。  
  
## 使用例  
 次の例では CS1108 が生成されます。  
  
```  
// cs1108.cs // Compile with: /target:library public class Test { // Regular Instance Method. public void TestMethod(ref out int i) {} // CS1108 }  
```