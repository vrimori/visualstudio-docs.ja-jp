---
title: "コンパイラ エラー CS0833 | Microsoft Docs"
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
  - "CS0833"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0833"
ms.assetid: 4ae32454-265f-47aa-bf2a-ee1d702330b7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0833
匿名型に、同じ名前を持つ複数のプロパティを含めることはできません  
  
 いずれの型とも同じように、匿名型でも 2 つのプロパティを同じ名前にすることはできません。  
  
### このエラーを解決するには  
  
1.  型の各プロパティに一意の名前を付けます。  
  
## 使用例  
 次の例では CS0833 が生成されます。  
  
```  
// cs0833.cs using System; public class C { public static int Main() { var c = new { p1 = 1, p1 = 2 }; // CS0833 return 1; } }  
```  
  
## 参照  
 [匿名型](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)