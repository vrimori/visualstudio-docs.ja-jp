---
title: "コンパイラ エラー CS1599 | Microsoft Docs"
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
  - "CS1599"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1599"
ms.assetid: 4cdb282d-0f5d-459b-afc1-8980fbb22067
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1599
メソッドまたはデリゲートは、型 'type' を返すことができません  
  
 .NET Framework クラス ライブラリの一部の型 \(<xref:System.TypedReference>、<xref:System.RuntimeArgumentHandle>、<xref:System.ArgIterator> など\) は、安全でない操作の実行に使用される可能性があるため、戻り値型として使用できません。  
  
 次の例では CS1599 が生成されます。  
  
```  
// CS1599.cs using System; class MyClass { public static void Main() { } public TypedReference Test1()   // CS1599 { return null; } public ArgIterator Test2()   // CS1599 { return null; } }  
```