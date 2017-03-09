---
title: "コンパイラの警告 (レベル 4) CS1573 | Microsoft Docs"
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
  - "CS1573"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1573"
ms.assetid: 1b68cb1a-9bfd-4343-b9b6-8ce195af5e23
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 4) CS1573
パラメーター 'parameter' には XML コメント内に 'parameter' に対応する param タグがありませんが、他のパラメーターにはあります  
  
 [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option) コンパイラ オプションを使用するときに、メソッドの一部のパラメーターにコメントが指定されましたが、すべてのパラメーターには指定されませんでした。 これらのパラメーターのコメントを入力し忘れた可能性があります。  
  
 次の例では CS1573 が生成されます。  
  
```  
// CS1573.cs // compile with: /W:4 public class MyClass { /// <param name='Int1'>Used to indicate status.</param> // enter a comment for Char1? public static void MyMethod(int Int1, char Char1) { } public static void Main () { } }  
```