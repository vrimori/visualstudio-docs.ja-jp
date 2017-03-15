---
title: "コンパイラ エラー CS1666 | Microsoft Docs"
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
  - "CS1666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1666"
ms.assetid: 4d62aa9c-71b9-4c6e-8141-2426d20ac243
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1666
fixed でない式に含まれる固定サイズ バッファーは使用できません。 fixed ステートメントを使用してください。  
  
 このエラーは、fixed でないクラスが含まれている式で固定サイズのバッファーを使用すると発生します。 ランタイムは、メモリ アクセスを最適化するために、fixed でないクラスを自由に移動します。これにより、固定サイズのバッファーを使用したときにエラーが発生することがあります。 このエラーを回避するには、ステートメントで `fixed` キーワードを使用します。  
  
## 使用例  
 次の例では CS1666 が生成されます。  
  
```  
// CS1666.cs // compile with: /unsafe /target:library unsafe struct S { public fixed int buffer[1]; } unsafe class Test { S field = new S(); private bool example1() { return (field.buffer[0] == 0);   // CS1666 error } private bool example2() { // OK fixed (S* p = &field) { return (p->buffer[0] == 0); } } private bool example3() { S local = new S(); return (local.buffer[0] == 0); } }  
```