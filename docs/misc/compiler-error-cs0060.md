---
title: "コンパイラ エラー CS0060 | Microsoft Docs"
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
  - "CS0060"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0060"
ms.assetid: ae6d4fb7-5ff9-4883-82c3-f55b190f439a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0060
アクセシビリティに一貫性がありません。基底クラス 'class1' のアクセシビリティはクラス 'class2' よりも低く設定されています。  
  
 クラスのアクセシビリティは、基底クラスと継承クラスの間で一貫している必要があります。  
  
 次の例では CS0060 が生成されます。  
  
```  
// CS0060.cs class MyClass // try the following line instead // public class MyClass { } public class MyClass2 : MyClass   // CS0060 { public static void Main() { } }  
```  
  
## 参照  
 [アクセス修飾子](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)