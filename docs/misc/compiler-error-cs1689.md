---
title: "コンパイラ エラー CS1689 | Microsoft Docs"
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
  - "CS1689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1689"
ms.assetid: 5fa6e845-40ef-4451-81ee-acbe2665527a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1689
属性 'Attribute Name' は、メソッドまたは属性クラスでのみ使用できます  
  
 このエラーは **ConditionalAttribute** 属性でのみ発生します。 メッセージにあるように、この属性はメソッドまたは属性クラスでのみ使用できます。 たとえば、この属性をクラスに適用しようとすると、このエラーが生成されます。  
  
## 使用例  
 次の例では CS1689 が生成されます。  
  
```  
// CS1689.cs // compile with: /target:library [System.Diagnostics.Conditional("A")]   // CS1689 class MyClass {}  
```