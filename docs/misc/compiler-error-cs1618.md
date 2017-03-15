---
title: "コンパイラ エラー CS1618 | Microsoft Docs"
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
  - "CS1618"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1618"
ms.assetid: e046d402-208e-48fd-8ff3-bb03044036c4
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1618
'method' は条件付き属性なので、この属性でデリゲートを作成できません  
  
 一部のビルドにメソッドが存在しない可能性があるため、条件付きメソッドを使用してデリゲートを作成することはできません。  
  
 次の例では CS1618 が生成されます。  
  
```  
// CS1618.cs using System; using System.Diagnostics; delegate void del(); class MakeAnError { public static void Main() { del d = new del(ConditionalMethod);   // CS1618 // Invalid because on builds where DEBUG is not set, // there will be no "ConditionalMethod". } // To fix the error, remove the next line: [Conditional("DEBUG")] public static void ConditionalMethod() { Console.WriteLine("Do something only in debug"); } }  
```