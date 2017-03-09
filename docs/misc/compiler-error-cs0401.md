---
title: "コンパイラ エラー CS0401 | Microsoft Docs"
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
  - "CS0401"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0401"
ms.assetid: 94eac5a8-7344-44d2-9d0c-a9954993603d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0401
new\(\) 制約は最後に指定する制約でなければなりません。  
  
 複数の制約を使用する場合は、new\(\) 制約の前にその他のすべての制約を列挙します。  
  
## 使用例  
 次の例では CS0401 が生成されます。  
  
```  
// CS0401.cs // compile with: /target:library using System; class C<T> where T : new(), IDisposable {}  // CS0401 class D<T> where T : IDisposable { static void F<U>() where U : new(), IDisposable{}   // CS0401 }  
```