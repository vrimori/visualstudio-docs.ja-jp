---
title: "コンパイラ エラー CS0687 | Microsoft Docs"
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
  - "CS0687"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0687"
ms.assetid: b51c5e7c-f4de-4aa4-97b1-ebe220cd19b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0687
名前空間エイリアス修飾子 '::' は、常に型または名前空間に解決するので、ここでは無効です 代わりに '.' を使用することを検討してください。  
  
 このエラーは、予期しない場所で、パーサーが型として解釈するものを使用した場合に発生します。 型または名前空間の名前は、メンバー アクセス \(**.**\) 演算子を使用して、メンバー アクセス式でのみ有効です。 これは、別のコンテキストでグローバル スコープ演算子 \(::\) を使用した場合に発生する可能性があります。  
  
## 使用例  
 次の例では CS0687 が生成されます。  
  
```  
// CS0687.cs using M = Test; using System; public class Test { public static int x = 77; public static void Main() { Console.WriteLine(M::x); // CS0687 // To resolve use the following line instead: // Console.WriteLine(M.x); } }  
```