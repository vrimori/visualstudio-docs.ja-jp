---
title: "コンパイラ エラー CS0023 | Microsoft Docs"
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
  - "CS0023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0023"
ms.assetid: 7a30073c-99de-41fa-ac6d-4a0dfbb76de9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0023
演算子 'operator' を 'type' 型のオペランドに適用することはできません  
  
 変数に演算子を適用しようとしましたが、変数の型は演算子に対して機能するように設計されていません。 詳細については、次のトピックを参照してください。[型](/dotnet/csharp/programming-guide/types/index) および[C\# 演算子](/dotnet/csharp/language-reference/operators/index).  
  
 次の例では CS0023 が生成されます。  
  
```  
// CS0023.cs namespace x { public class a { public static void Main() { string s = "hello"; s = -s;   // CS0023, minus operator not allowed on strings } } }  
```