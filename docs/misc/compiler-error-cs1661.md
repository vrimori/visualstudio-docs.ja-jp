---
title: "コンパイラ エラー CS1661 | Microsoft Docs"
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
  - "CS1661"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1661"
ms.assetid: 162d5736-ca3c-4a09-a5d9-a19da3d5bf24
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1661
指定されたブロックのパラメーター型がデリゲート パラメーター型と一致しないため、匿名メソッド ブロックをデリゲート型 'delegate type' に変換することはできません。  
  
 匿名メソッドの定義で匿名メソッドのパラメーター型がデリゲート パラメーター型と一致しない場合にこのエラーが生じます。 パラメーター数、パラメーター型、ref または out パラメーターを確認し、完全に一致することを確かめてください。  
  
 次の例では CS1661 が生成されます。  
  
```  
// CS1661.cs delegate void MyDelegate(int i); class C { public static void Main() { MyDelegate d = delegate(string s) { };  // CS1661 } }  
```