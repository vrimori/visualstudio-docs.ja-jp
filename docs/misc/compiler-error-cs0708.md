---
title: "コンパイラ エラー CS0708 | Microsoft Docs"
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
  - "CS0708"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0708"
ms.assetid: 19e1907f-b78c-4c8b-b78c-eedfd57115f2
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0708
'field': 静的クラスでインスタンス メンバーを宣言することはできません  
  
 このエラーは、静的に宣言されているクラスで非静的メンバーを宣言すると発生します。 静的クラスのインスタンスを作成できないため、インスタンス変数が無意味になります。**static** キーワードは、静的クラスのすべてのメンバーに適用されます。  
  
 次の例では CS0708 が生成されます。  
  
```  
// CS0708.cs // compile with: /target:library public static class C { int i;  // CS0708 static int j;  // OK }  
```