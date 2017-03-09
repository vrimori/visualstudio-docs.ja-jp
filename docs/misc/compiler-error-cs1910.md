---
title: "コンパイラ エラー CS1910 | Microsoft Docs"
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
  - "CS1910"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1910"
ms.assetid: 0fef9727-e56f-451c-9255-ca4e5a26d7c6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1910
型 'type' の引数は、DefaultValue 属性には適用できません。  
  
 型がオブジェクトのパラメーターの場合、<xref:System.Runtime.InteropServices.DefaultParameterValueAttribute> の引数は `null`、整数型、浮動小数点、`bool`、`string`、`enum`、または `char` である必要があります。 引数を型 <xref:System.Type> または任意の配列型にすることはできません。  
  
## 使用例  
 次の例では CS1910 が生成されます。  
  
```  
// CS1910.cs // compile with: /target:library using System.Runtime.InteropServices; public interface MyI { void Test([DefaultParameterValue(typeof(object))] object o);   // CS1910 }  
```