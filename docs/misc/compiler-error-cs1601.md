---
title: "コンパイラ エラー CS1601 | Microsoft Docs"
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
  - "CS1601"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1601"
ms.assetid: 5efa1d2d-c70c-446d-a51f-d23d8a3be22e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1601
メソッドまたはデリゲート パラメーターを型 'type' にすることはできません  
  
 .NET Framework クラス ライブラリの一部の型 \(<xref:System.TypedReference>、<xref:System.RuntimeArgumentHandle>、<xref:System.ArgIterator> など\) は、安全でない操作の実行に使用される可能性があるため、[ref](/dotnet/csharp/language-reference/keywords/ref) パラメーターや [out](/dotnet/csharp/language-reference/keywords/out) パラメーターとしては使用できません。  
  
 次の例では CS1601 が生成されます。  
  
```  
// CS1601.cs using System; class MyClass { public void Test1 (ref TypedReference t)   // CS1601 { } public void Test2 (out ArgIterator t)   // CS1601 { } }  
```