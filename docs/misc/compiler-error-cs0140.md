---
title: "コンパイラ エラー CS0140 | Microsoft Docs"
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
  - "CS0140"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0140"
ms.assetid: 61787b8a-7b69-41c1-8ee3-87f619698594
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0140
ラベル 'label' は重複しています。  
  
 同じ名前のラベルが 2 回使用されています。 詳細については、「[goto](/dotnet/csharp/language-reference/keywords/goto)」を参照してください。  
  
 次の例では CS0140 が生成されます。  
  
```  
// CS0140.cs namespace MyNamespace { public class MyClass { public static void Main() { label1: int i = 0; label1: int j = 0;   // CS0140, comment this line to resolve goto label1; } } }  
```