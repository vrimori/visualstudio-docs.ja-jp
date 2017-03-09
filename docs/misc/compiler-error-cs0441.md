---
title: "コンパイラ エラー CS0441 | Microsoft Docs"
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
  - "CS0441"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0441"
ms.assetid: 3f07500a-d479-424c-a0f4-c219be1b5a45
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0441
'class': クラスに static と sealed の両方を指定することはできません。  
  
 このエラーは、static と sealed の両方であるクラスを宣言すると発生します。 静的クラスは本質的にシールされているため、sealed 修飾子が必要ではありません。 解決するには、いずれかの修飾子を使用します。  
  
 次の例では、CS0441 が生成されます。  
  
```  
// CS0441.cs sealed static class MyClass { }   // CS0441  
```