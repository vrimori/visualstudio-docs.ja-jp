---
title: "コンパイラ エラー CS1597 | Microsoft Docs"
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
  - "CS1597"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1597"
ms.assetid: 735e7cde-38de-4e15-96cc-ce75ffe34ff2
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1597
メソッドまたはアクセサー ブロックの後のセミコロンの使用が正しくありません。  
  
 メソッドまたはアクセサー ブロックの終了に、セミコロンは不要です \(または許可されていません\)。  
  
 次の例では CS1597 が生成されます。  
  
```  
// CS1597.cs class TestClass { public static void Main() { };   // CS1597, remove semicolon }  
```