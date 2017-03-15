---
title: "コンパイラ エラー CS0058 | Microsoft Docs"
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
  - "CS0058"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0058"
ms.assetid: 9535da60-03b9-41ab-93e1-e57b6440fca9
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0058
アクセシビリティに一貫性がありません。戻り値の型 'type' のアクセシビリティはデリゲート 'delegate' よりも低く設定されています  
  
 パブリック コンストラクトは、パブリックにアクセスできるオブジェクトを返す必要があります。 詳細については、「[アクセス修飾子](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)」を参照してください。  
  
 次の例では、MyClass にアクセス修飾子が適用されず、したがって既定でプライベート アクセシビリティを与えられるため、CS0058 が生成されます。  
  
```  
// CS0058.cs class MyClass // try the following line instead // public class MyClass { } public delegate MyClass MyClassDel();   // CS0058 public class A { public static void Main() { } }  
```  
  
## 参照  
 [private](/dotnet/csharp/language-reference/keywords/private)