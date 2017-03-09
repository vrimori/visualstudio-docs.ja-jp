---
title: "コンパイラ エラー CS0459 | Microsoft Docs"
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
  - "CS0459"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0459"
ms.assetid: 01b058dd-8d65-4e9d-9de1-d47f9488d22a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0459
読み取り専用のローカル変数のアドレスを取得することはできません。  
  
 読み取り専用のローカル変数 `foreach`、`using`、および `fixed` を C\# 言語で生成するには、3 つのシナリオがあります。 これらそれぞれの場合において、読み取り専用のローカル変数に書き込んだり、そのアドレスを取得したりすることはできません。 このエラーは、読み取り専用のローカル変数のアドレスを取得しようとしていることが、コンパイラで認識されたときに生成されます。  
  
## 使用例  
 次の例では、`foreach` ループおよび `fixed` ステートメント ブロック内に含まれる読み取り専用ローカル変数のアドレスの取得が試行されたときに、CS0459 が生成されます。  
  
```  
// CS0459.cs // compile with: /unsafe class A { public unsafe void M1() { int[] ints = new int[] { 1, 2, 3 }; foreach (int i in ints) { int *j = &i;  // CS0459 } fixed (int *i = &_i) { int **j = &i;  // CS0459 } } private int _i = 0; }  
```