---
title: "コンパイラ エラー CS0283 | Microsoft Docs"
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
  - "CS0283"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0283"
ms.assetid: f94a5b84-92c5-4602-894d-6f856d57e0e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0283
型 'type' を const 宣言することはできません  
  
 定数宣言で指定された型は、`byte`、`char`、`short`、`int`、`long`、`float`、`double`、`decimal`、`bool`、`string`、列挙型、または null 値が割り当てられている参照型である必要があります。 各定数式では、対象の型の値、または暗黙的な変換によって対象の型に変換できる型の値を生成する必要があります。  
  
## 使用例  
 次の例では CS0283 が生成されます。  
  
```  
// CS0283.cs struct MyTest { } class MyClass { // To resolve the error but retain the "const-ness", // change const to readonly. const MyTest test = new MyTest();   // CS0283 public static int Main() { return 1; } }  
```