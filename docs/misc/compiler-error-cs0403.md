---
title: "コンパイラ エラー CS0403 | Microsoft Docs"
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
  - "CS0403"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0403"
ms.assetid: 6e5d55ce-d6bf-419d-aded-aaa2e5963bb6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0403
Null 非許容の値型である可能性があるため、Null を型パラメーター 'name' に変換できません。 代わりに default\('T'\) を使用してください。  
  
 指定された不明な型は Null の代入が許可されない値型である可能性があるため、この型には Null を代入できません。 ジェネリック クラスが値型を受け取るものではない場合は、クラス型制約を使用します。 組み込み型などの値型を受け取ることができる場合は、次の例に示すように、Null への代入を式 `default(T)` で置き換えることができる場合があります。  
  
## 使用例  
 次の例では CS0403 が生成されます。  
  
```  
// CS0403.cs // compile with: /target:library class C<T> { public void f() { T t = null;  // CS0403 T t2 = default(T);   // OK } } class D<T> where T : class { public void f() { T t = null;  // OK } }  
```