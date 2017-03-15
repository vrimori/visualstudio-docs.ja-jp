---
title: "コンパイラ エラー CS0762 | Microsoft Docs"
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
  - "CS0762"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0762"
ms.assetid: 7cedd1af-ffe6-4ca7-82fb-faa9e98014a4
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0762
メソッド 'method' は実装宣言がない部分メソッドであるため、このメソッドからデリゲートを作成できません  
  
 部分メソッドには、実装宣言は必要ありません。 ただし、デリゲートのカプセル化されたメソッドには実装が必要です。  
  
### このエラーを解決するには  
  
1.  デリゲートを初期化するために使用されるメソッドの実装を提供します。  
  
## 使用例  
  
```  
public delegate void TestDel(); public partial class C { partial void Part(); public static int Main() { C c = new C(); TestDel td = new TestDel(c.Part); // CS0762 return 1; } }  
```