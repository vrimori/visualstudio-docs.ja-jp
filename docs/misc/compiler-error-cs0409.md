---
title: "コンパイラ エラー CS0409 | Microsoft Docs"
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
  - "CS0409"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0409"
ms.assetid: 23d86c13-7978-41b7-a087-ffcea52476fa
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0409
型パラメーター 'type parameter' に対して、制約句は既に指定されています。 型パラメーターのすべての制約は、1 つの場所で指定する必要があります。  
  
 1 つの型パラメーターに対して、複数の制約句 \(where 句\) が見つかりました。 余分な where 句を削除するか、それぞれの句内の型パラメーターが一意になるように where 句を修正します。  
  
```  
// CS0409.cs interface I { } class C<T1, T2> where T1 : I where T1 : I  // CS0409 – T1 used twice { }  
```