---
title: "コンパイラ エラー CS1012 | Microsoft Docs"
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
  - "CS1012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1012"
ms.assetid: 4acc5fe0-da47-4882-b7d8-557767d7cf03
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1012
文字リテラルに文字が多すぎます。  
  
 複数の文字で [char](/dotnet/csharp/language-reference/keywords/char) 定数を初期化しようとしました。  
  
 CS1012 は、データ バインディングの実行時にも発生することがあります。 たとえば、次の行はエラーになります。  
  
 `<%# DataBinder.Eval(Container.DataItem, 'doctitle') %>`  
  
 代わりに、次の行を試してください。  
  
 `<%# DataBinder.Eval(Container.DataItem, "doctitle") %>`  
  
 次の例では CS1012 が生成されます。  
  
```  
// CS1012.cs class Sample { static void Main() { char a = 'xx';   // CS1012 char a2 = 'x';   // OK System.Console.WriteLine(a2); } }  
```