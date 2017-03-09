---
title: "コンパイラの警告 (レベル 2) CS0253 | Microsoft Docs"
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
  - "CS0253"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0253"
ms.assetid: e02d5dac-c2d9-45ca-9dd3-dda06c96f4d6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS0253
予期しない参照比較です。比較値を取得するには型 'type' に右辺をキャストしてください  
  
 コンパイラが参照比較を行っています。 文字列の値を比較する場合は、式の右辺を `type` にキャストしてください。  
  
 次の例では CS0253 が生成されます。  
  
```  
// CS0253.cs // compile with: /W:2 using System; class MyClass { public static void Main() { string s = "11"; object o = s + s; bool c = s == o;   // CS0253 // try the following line instead // bool c = s == (string)o; } }  
```