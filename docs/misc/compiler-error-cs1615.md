---
title: "コンパイラ エラー CS1615 | Microsoft Docs"
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
  - "CS1615"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1615"
ms.assetid: 518bb07f-0e3a-4761-9931-66845eb5df1a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1615
引数 'number' を 'keyword' キーワードと共に渡すことはできません  
  
 引数に `ref` または **out** パラメーターを受け取らない関数で、キーワード `ref` または **out** のどちらかが使用されました。 このエラーを解決するには、正しくないキーワードを削除し、関数の宣言と一致する適切なキーワードを使用します \(存在する場合\)。  
  
 次の例では CS1615 が生成されます。  
  
```  
// CS1615.cs class C { public void f(int i) {} public static void Main() { int i = 1; f(ref i);  // CS1615 } }  
```