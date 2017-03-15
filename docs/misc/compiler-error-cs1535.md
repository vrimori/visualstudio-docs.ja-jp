---
title: "コンパイラ エラー CS1535 | Microsoft Docs"
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
  - "CS1535"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1535"
ms.assetid: 19f41e78-9aea-4575-abd0-60ddb927276f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1535
オーバーロードされた単項演算子 'operator' に指定できるパラメーター数は 1 です。  
  
 単項の[オーバーロード可能な演算子](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators)の定義では、1 つのパラメーターを取る必要があります。  
  
## 使用例  
 次の例では CS1535 が生成されます。  
  
```  
// CS1535.cs class MyClass { // uncomment the method parameter to resolve CS1535 public static MyClass operator ++ (/*MyClass MC1*/)   // CS1535 { return new MyClass(); } public static int Main() { return 1; } }  
```