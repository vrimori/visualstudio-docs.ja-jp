---
title: "コンパイラの警告 (レベル 3) CS0661 | Microsoft Docs"
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
  - "CS0661"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0661"
ms.assetid: c218665e-5947-40bb-b633-d268483e6522
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 3) CS0661
'class' が演算子 \=\= または演算子 \!\= を定義していますが、Object.GetHashCode\(\) をオーバーライドしていません  
  
 コンパイラがユーザー定義の等値演算子または非等値演算子を検出しましたが、**GetHashCode** 関数のオーバーライドが設定されていません。 ユーザー定義の等値演算子または非等値演算子は、**GetHashCode** 関数をオーバーライドする場合に使用します。  
  
 次の例では CS0661 が生成されます。  
  
```  
// CS0661.cs // compile with: /W:3 class Test   // CS0661 { public static bool operator == (object o, Test t) { return true; } public static bool operator != (object o, Test t) { return true; } public override bool Equals(object o) { return true; } // uncomment the GetHashCode function to resolve // public override int GetHashCode() // { //    return 0; // } public static void Main() { } }  
```