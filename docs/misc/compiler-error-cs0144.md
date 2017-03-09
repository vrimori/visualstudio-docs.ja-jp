---
title: "コンパイラ エラー CS0144 | Microsoft Docs"
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
  - "CS0144"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0144"
ms.assetid: 3904cab1-05bd-44ec-81d0-e36c5656f742
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0144
抽象クラスまたはインターフェイス 'interface' のインスタンスを作成できません  
  
 [抽象](/dotnet/csharp/language-reference/keywords/abstract)クラスまたは[インターフェイス](/dotnet/csharp/language-reference/keywords/interface) 'interface' のインスタンスを作成できません。 詳細については、「[インターフェイス](/dotnet/csharp/programming-guide/interfaces/index)」を参照してください。  
  
 次の例では CS0144 が生成されます。  
  
```  
// CS0144.cs interface MyInterface { } public class MyClass { public static void Main() { MyInterface myInterface = new MyInterface ();   // CS0144 } }  
```