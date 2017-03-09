---
title: "コンパイラ エラー CS0306 | Microsoft Docs"
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
  - "CS0306"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0306"
ms.assetid: f340a3ce-6140-4001-bb00-628a2985ddd6
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0306
型 'type' は型引数に使用できません  
  
 型パラメーターとして使用された型は許可されていません。 型がポインター型である可能性があります。  
  
 次の例では CS0306 が生成されます。  
  
```  
// CS0306.cs class C<T> { } class M { // CS0306 – int* not allowed as a type parameter C<int*> f; }  
```