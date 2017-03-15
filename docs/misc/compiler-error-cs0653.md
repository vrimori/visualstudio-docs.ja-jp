---
title: "コンパイラ エラー CS0653 | Microsoft Docs"
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
  - "CS0653"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0653"
ms.assetid: c94043b9-b5d9-4294-921d-a4aead124d44
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0653
抽象であるため属性クラス 'class' を適用でません  
  
 [abstract](/dotnet/csharp/language-reference/keywords/abstract) カスタム属性クラスは、属性として使用できません。  
  
 次の例では CS0653 が生成されます。  
  
```  
// CS0653.cs using System; public abstract class MyAttribute : Attribute { } public class My2Attribute : MyAttribute { } [My]   // CS0653 // try the following line instead // [My2] class MyClass { public static void Main() { } }  
```