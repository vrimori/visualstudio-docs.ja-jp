---
title: "コンパイラ エラー CS0527 | Microsoft Docs"
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
  - "CS0527"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0527"
ms.assetid: 1acd244b-c55b-424f-b038-a130d65b8685
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0527
インターフェイス リストの型 'type' はインターフェイスではありません  
  
 [struct](/dotnet/csharp/language-reference/keywords/struct) または [interface](/dotnet/csharp/language-reference/keywords/interface) は、別のインターフェイスから継承できますが、他の型から継承することはできません。  
  
 次の例では CS0527 が生成されます。  
  
```  
// CS0527.cs // compile with: /target:library public struct clx : int {}   // CS0527 int not an interface  
```