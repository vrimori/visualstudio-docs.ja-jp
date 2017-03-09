---
title: "コンパイラ エラー CS0262 | Microsoft Docs"
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
  - "CS0262"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0262"
ms.assetid: 44f8661f-c934-483f-84cd-00ca8257e50a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0262
'type' の partial 宣言には競合するアクセシビリティ修飾子が含まれています  
  
 このエラーは、部分型の修飾子 \(public、private、protected、internal、abstract など\) に一貫性がない場合に発生します。 その型のすべての partial 宣言でこれらの修飾子が一貫している必要があります。 詳細については、「[部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)」を参照してください。  
  
## 使用例  
 次の例では CS0262 が生成されます。  
  
```  
// CS0262.cs class A { public partial class C  // CS0262 { } private partial class C { } }  
```