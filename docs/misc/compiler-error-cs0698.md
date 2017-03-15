---
title: "コンパイラ エラー CS0698 | Microsoft Docs"
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
  - "CS0698"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0698"
ms.assetid: 68211652-fdfa-4d37-9451-f0b4238f9fe6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0698
ジェネリック型は属性クラスであるため、'class' から派生できません  
  
 属性クラスから派生するクラスは、すべて属性です。 属性は、ジェネリック型にすることはできません。  
  
 次の例では CS0698 が生成されます。  
  
```  
// CS0698.cs class C<T> : System.Attribute  // CS0698 { }  
```