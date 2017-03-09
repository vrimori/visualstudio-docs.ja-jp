---
title: "コンパイラの警告 (レベル 4) CS0649 | Microsoft Docs"
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
  - "CS0649"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0649"
ms.assetid: 37137b18-12ed-4a0f-92e6-ee5fb0532ef3
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 4) CS0649
フィールド 'field' は割り当てられません。常に既定値 'value' を使用します  
  
 値が割り当てられていない、初期化されていないプライベート フィールドまたは内部フィールドの宣言が検出されました。  
  
 次の例では CS0649 が生成されます。  
  
```  
// CS0649.cs // compile with: /W:4 using System.Collections; class MyClass { Hashtable table;  // CS0649 // You may have intended to initialize the variable to null // Hashtable table = null; // Or you may have meant to create an object here // Hashtable table = new Hashtable(); public void Func(object o, string p) { // Or here // table = new Hashtable(); table[p] = o; } public static void Main() { } }  
```