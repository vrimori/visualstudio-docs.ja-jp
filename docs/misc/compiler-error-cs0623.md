---
title: "コンパイラ エラー CS0623 | Microsoft Docs"
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
  - "CS0623"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0623"
ms.assetid: c9fd6888-b9c5-48bf-b25b-2fae1446ad24
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0623
配列初期化子は変数かフィールド初期化子の中でのみ使用できます。 代わりに、新しい式を使用してください。  
  
 許可されていないコンテキストで配列初期化子を使用して配列を初期化しようとしました。  
  
## 使用例  
 次の例では、コンパイラは \\{4\\} を外部配列初期化子の内部に埋め込まれた配列初期化子として解釈するため、CS0623 が生成されます。  
  
```  
//cs0632.cs using System; class X { public int[] x = { 2, 3, {4}}; //CS0623 }  
```  
  
## 参照  
 [配列](/dotnet/csharp/programming-guide/arrays/index)