---
title: "コンパイラ エラー CS1511 | Microsoft Docs"
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
  - "CS1511"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1511"
ms.assetid: c04b5268-5bc3-41db-af6b-463ab1d802b4
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1511
キーワード 'base' は静的メソッドでは使用できません。  
  
 [base](/dotnet/csharp/language-reference/keywords/base) キーワードが [static](/dotnet/csharp/language-reference/keywords/static) メソッドで使用されました。`base` は、インスタンス コンストラクター、インスタンス メソッド、またはインスタンス アクセサーでのみ呼び出すことができます。  
  
## 使用例  
 次の例では CS1511 が生成されます。  
  
```  
// CS1511.cs // compile with: /target:library public class A { public int j = 0; } class C : A { public void Method() { base.j = 3;   // base allowed here } public static int StaticMethod() { base.j = 3;   // CS1511 return 1; } }  
```