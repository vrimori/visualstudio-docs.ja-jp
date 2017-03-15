---
title: "コンパイラ エラー CS1913 | Microsoft Docs"
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
  - "CS1913"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1913"
ms.assetid: 652494b3-9576-4a4c-a9ee-695f86c4a023
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1913
メンバー 'name' はフィールドでもプロパティでもないため、 初期化することはできません。  
  
 オブジェクト初期化子は、アクセス可能なフィールドまたはプロパティを初期化するためにのみ使用できます。  
  
### このエラーを解決するには  
  
1.  通常のコンストラクターまたはその他の初期化メソッドで、クラス メンバーを初期化します。  
  
## 使用例  
 次の例では、CS1913 が生成されます。  
  
```  
// cs1912.cs class A { public delegate void D(); public event D myEvent; } public class Test { static void Main() { A a = new A() {myEvent = M}; // CS1913 } public void M(){} }  
```  
  
## 参照  
 [クラスと構造体](/dotnet/csharp/programming-guide/classes-and-structs/index)