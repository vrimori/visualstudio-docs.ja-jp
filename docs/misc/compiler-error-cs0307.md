---
title: "コンパイラ エラー CS0307 | Microsoft Docs"
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
  - "CS0307"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0307"
ms.assetid: 202a9985-ed7a-4e0a-9573-5624e066d314
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0307
'construct' 'identifier' は、ジェネリック メソッドではありません。 式リストを意図した場合は、\< 式をかっこで囲んでください。  
  
 名前の挙げられたコンストラクトは、ジェネリック引数を取得可能なただ 1 つのコンストラクトである、型またはメソッドではありませんでした。 山かっこ内の型引数を削除します。 ジェネリックが必要な場合は、ジェネリック型またはメソッドとしてジェネリック コンストラクトを宣言します。  
  
 次の例では CS0307 が生成されます。  
  
```  
// CS0307.cs class C { public int P { get { return 1; } } public static void Main() { C c = new C(); int p = c.P<int>();  // CS0307 – C.P is a property // Try this instead // int p = c.P; } }  
```