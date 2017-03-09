---
title: "コンパイラ エラー CS1011 | Microsoft Docs"
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
  - "CS1011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1011"
ms.assetid: d4568471-b0f8-4c24-89f3-9c543521d1d8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1011
空の文字リテラルです。  
  
 [char](/dotnet/csharp/language-reference/keywords/char) が宣言され、null に初期化されました。`char` の初期化では、文字を指定する必要があります。  
  
 次の例では CS1011 が生成されます。  
  
```  
// CS1011.cs class Sample { public char CharField = '';   // CS1011 }  
```