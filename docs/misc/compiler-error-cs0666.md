---
title: "コンパイラ エラー CS0666 | Microsoft Docs"
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
  - "CS0666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0666"
ms.assetid: 44ad4574-b4a2-487b-8d05-0116762231ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0666
'member': 新規のプロテクト メンバーが構造体で宣言されています  
  
 [struct](/dotnet/csharp/language-reference/keywords/struct) を [abstract](/dotnet/csharp/language-reference/keywords/abstract) にすることはできず、常に暗黙的にシール \([sealed](/dotnet/csharp/language-reference/keywords/sealed)\) されます。 struct は、継承をサポートしていないため、struct の [protected](/dotnet/csharp/language-reference/keywords/protected) メンバーの概念は意味がありません。 詳細については、「[継承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)」を参照してください。  
  
## 使用例  
 次の例では CS0666 が生成されます。  
  
```  
// CS0666.cs class M { static void Main() { } } struct S { protected int x;   // CS0666 }  
```