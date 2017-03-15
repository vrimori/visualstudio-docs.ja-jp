---
title: "コンパイラの警告 (レベル 4) CS0628 | Microsoft Docs"
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
  - "CS0628"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0628"
ms.assetid: a54cfad8-27c9-4abb-8c83-982615489a10
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 4) CS0628
'member': 新規のプロテクト メンバーがシール クラスで宣言されました  
  
 他のクラスは `sealed` クラスから継承できず、`protected` メンバーを使用することができないため、[シール](/dotnet/csharp/language-reference/keywords/sealed) クラスは[プロテクト](/dotnet/csharp/language-reference/keywords/protected) メンバーを使用できません。  
  
 次の例では CS0628 が生成されます。  
  
```  
// CS0628.cs // compile with: /W:4 sealed class C { protected int i;   // CS0628 } class MyClass { public static void Main() { } }  
```