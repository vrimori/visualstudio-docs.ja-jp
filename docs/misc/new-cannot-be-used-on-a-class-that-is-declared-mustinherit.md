---
title: "&#39;MustInherit&#39; として宣言されたクラスでは、&#39;New&#39; を使用することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30569"
  - "bc30569"
helpviewer_keywords: 
  - "BC30569"
ms.assetid: 94c9e6a3-6489-4d58-b7e5-7b4203677e3b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MustInherit&#39; として宣言されたクラスでは、&#39;New&#39; を使用することはできません
`MustInherit` クラスを直接インスタンス化することはできないため、`MustInherit` クラスで `New` 演算子は使用できません。 コンパイル時の型が `MustInherit` である変数と値を持つはできますが、このような変数と値は null 値であるか、または `MustInherit` 型から派生した通常のクラスのインスタンスへの参照を含むかのどちらかである必要があります。  
  
 **エラー ID:** BC30569  
  
### このエラーを解決するには  
  
-   `New` 演算子を削除します。  
  
## 参照  
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)