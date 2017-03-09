---
title: "コンパイラ エラー CS0662 | Microsoft Docs"
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
  - "CS0662"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0662"
ms.assetid: 836fa15e-3bf3-4af5-8acf-072d7d731dcd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0662
'method' は ref パラメーターの Out 属性だけを指定することはできません。 In 属性と Out 属性の両方を使用するか、どちらも使用しないでください。  
  
 インターフェイス メソッドには、[Out](frlrfSystemRuntimeInteropServicesOutAttributeClassTopic) 属性だけで [ref](/dotnet/csharp/language-reference/keywords/ref) を使用するパラメーターがあります。**Out** 属性を使用する `ref` パラメーターでは、[In](frlrfSystemRuntimeInteropServicesInAttributeClassTopic) 属性も使用する必要があります。  
  
 次の例では CS0662 が生成されます。  
  
```  
// CS0662.cs using System.Runtime.InteropServices; interface I { void method([Out] ref int i);   // CS0662 // try one of the following lines instead // void method(ref int i); // void method([Out, In]ref int i); } class test { public static void Main() { } }  
```