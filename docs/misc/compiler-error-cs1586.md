---
title: "コンパイラ エラー CS1586 | Microsoft Docs"
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
  - "CS1586"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1586"
ms.assetid: 408a4495-6fe6-4e95-a49f-a4d041675fff
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1586
配列を作成するには、配列のサイズまたは配列の初期化子を指定する必要があります。  
  
 配列の宣言が正しくありません。  
  
 次の例では CS1586 が生成されます。  
  
```  
// CS1586.cs using System; class MyClass { public static void Main() { int[] a = new int[];   // CS1586 // try the following line instead int[] b = new int[5]; } }  
```  
  
## 参照  
 [配列](/dotnet/csharp/programming-guide/arrays/index)