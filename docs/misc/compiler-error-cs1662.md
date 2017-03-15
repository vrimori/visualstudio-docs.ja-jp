---
title: "コンパイラ エラー CS1662 | Microsoft Docs"
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
  - "CS1662"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1662"
ms.assetid: e61a4fc8-0ef1-4a4a-a27b-3a015c3ba38a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1662
デリゲート戻り値の型に暗黙的に変換できない戻り値の型がブロック内にあるため、匿名メソッド ブロックをデリゲート型 'delegate type' に変換することはできません。  
  
 このエラーは、匿名メソッド ブロックの return ステートメントに、デリゲートの戻り値の型に暗黙的に変換できない型が存在する場合に発生します。  
  
 次の例では CS1662 が生成されます。  
  
```  
// CS1662.cs delegate int MyDelegate(int i); class C { public static void Main() { MyDelegate d = delegate(int i) { return 1.0; };  // CS1662 // Try this instead: // MyDelegate d = dekegate(int i) { return (int)1.0; }; } }  
```