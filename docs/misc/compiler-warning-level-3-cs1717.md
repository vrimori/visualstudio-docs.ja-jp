---
title: "コンパイラの警告 (レベル 3) CS1717 | Microsoft Docs"
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
  - "CS1717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1717"
ms.assetid: 5b150a2c-5d61-4cd8-b4d4-e6c2b93b52c6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 3) CS1717
同じ変数に割り当てられました。他の変数に割り当てますか?  
  
 この警告は、`a = a` のように変数をそれ自体に代入したときに発生します。  
  
 いくつかの一般的なミスにより、この警告が生成されることがあります。  
  
-   **if** ステートメントの条件として `a = a` と記述した場合 \(例: `if (a = a)`\)。 本来は `if (a == a)` と記述するつもりであったケースで、この式は常に true になるため、より簡潔に `if (true)` と記述することもできます。  
  
-   入力ミス。 本来は `a = b` と記述するつもりであったケース。  
  
-   パラメーターがフィールドと同じ名前を持ち、**this** キーワードを使用していないコンストラクター。本来は `this.a = a` と記述するつもりであったケース。  
  
## 使用例  
 次の例では CS1717 が生成されます。  
  
```  
// CS1717.cs // compile with: /W:3 public class Test { public static void Main() { int x = 0; x = x;   // CS1717 } }  
```