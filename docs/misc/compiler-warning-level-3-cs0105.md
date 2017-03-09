---
title: "コンパイラの警告 (レベル 3) CS0105 | Microsoft Docs"
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
  - "CS0105"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0105"
ms.assetid: 96d1d5d7-79e9-424f-bbde-f87e88b70003
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 3) CS0105
'namespace' の using ディレクティブは、この名前空間で既に使用されています。  
  
 1 回のみ宣言する必要のある[名前空間](/dotnet/csharp/language-reference/keywords/namespace)が、複数回宣言されました。すべての重複する名前空間宣言を削除します。  
  
 次の例では CS0105 が生成されます。  
  
```  
// CS0105.cs // compile with: /W:3 using System; using System;   // CS0105 public class a { public static void Main() { } }  
```