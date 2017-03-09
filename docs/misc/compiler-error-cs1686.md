---
title: "コンパイラ エラー CS1686 | Microsoft Docs"
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
  - "CS1686"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1686"
ms.assetid: 46a9e82b-57f4-416d-8e49-242bfff5433a
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1686
ローカル 'variable' またはそのメンバーが、アドレスを取得することができず、匿名メソッドまたはラムダ式の内部で使用することができません  
  
 このエラーは、変数を使用したり、そのアドレスを取得しようとしたりした場合や、これらのアクションのいずれかが匿名メソッド内で実行された場合に発生します。  
  
## 使用例  
 次の例では CS1686 が生成されます。  
  
```  
// CS1686.cs // compile with: /unsafe /target:library class MyClass { public unsafe delegate int * MyDelegate(); public unsafe int * Test() { int j = 0; MyDelegate d = delegate { return &j; };   // CS1686 return &j;   // OK } }  
```