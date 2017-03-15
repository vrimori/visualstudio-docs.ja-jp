---
title: "&#39;Declare&#39; ステートメントは、ジェネリック型またはジェネリック型に含まれる型では使用できません | Microsoft Docs"
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
  - "BC32075"
  - "vbc32075"
helpviewer_keywords: 
  - "BC32075"
ms.assetid: c620b67e-70f8-42ac-8292-e9ea484904c3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Declare&#39; ステートメントは、ジェネリック型またはジェネリック型に含まれる型では使用できません
`Declare` ステートメントが、ジェネリック クラスまたは構造体の一部に含まれているか、ジェネリック クラスまたは構造体の中で宣言されているクラスまたは構造体の一部に含まれています。  
  
 Visual Basic と .NET Framework は、現時点では外部参照とジェネリック型の組み合わせをサポートしていません。 コンパイラで外部プロシージャを正しく呼び出すには、この外部プロシージャのすべてのパラメーターと戻り値の型が必要です。  
  
 **エラー ID:** BC32075  
  
### このエラーを解決するには  
  
-   `Declare` ステートメントをジェネリック型のスコープ外に移動するか、完全に削除します。  
  
## 参照  
 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)