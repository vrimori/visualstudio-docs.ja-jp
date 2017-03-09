---
title: "コンパイラ エラー CS1013 | Microsoft Docs"
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
  - "CS1013"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1013"
ms.assetid: e5b1d24d-e558-4f7c-b2b1-3a644710005d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1013
無効な数値です。  
  
 正しくない形式の数値が検出されました。 整数型の詳細については、「[整数型の一覧表](/dotnet/csharp/language-reference/keywords/integral-types-table)」を参照してください。  
  
## 使用例  
 次の例では CS1013 が生成されます。  
  
```  
// CS1013.cs class Sample { static void Main() { int i = 0x;   // CS1013 } }  
```