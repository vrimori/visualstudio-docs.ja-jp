---
title: "コンパイラ エラー CS1908 | Microsoft Docs"
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
  - "CS1908"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1908"
ms.assetid: d7da31c2-48ef-4401-b885-3459b4d7f6f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1908
DefaultValue 属性への引数の型は、パラメーター型と一致していることが必要です。  
  
 このエラーは、<xref:System.ComponentModel.DefaultValueAttribute> 属性値に誤った引数を使用すると生成されます。 パラメーターの型に一致する値を使用します。  
  
## 使用例  
 次の例では CS1908 が生成されます。  
  
```  
// CS1908.cs // compile with: /target:library using System.Runtime.InteropServices; public interface ISomeInterface { void Bad([Optional] [DefaultParameterValue("true")] bool b);   // CS1908 void Good([Optional] [DefaultParameterValue(true)] bool b);   // OK }  
```