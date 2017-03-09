---
title: "パラメーター &#39;&lt;parametername&gt;&#39; と一致する引数は &#39;&lt;type1&gt;&#39; から &#39;&lt;type2&gt;&#39; へ縮小変換します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30520"
  - "bc30520"
helpviewer_keywords: 
  - "BC30520"
ms.assetid: 652ff70b-156d-4d1c-af19-fa1c53e2d0b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# パラメーター &#39;&lt;parametername&gt;&#39; と一致する引数は &#39;&lt;type1&gt;&#39; から &#39;&lt;type2&gt;&#39; へ縮小変換します。
オーバーロードされたメソッドを呼び出しましたが、コンパイラで、縮小変換せずに呼び出すことのできるメソッドを検出できません。 縮小変換により、有効値の一部を正確に保持できない可能性のあるデータ型に値が変更されます。  
  
 **エラー ID:** BC30520  
  
### このエラーを解決するには  
  
-   `Option Strict Off` を指定します。  
  
## 参照  
 [Overloaded Properties and Methods](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)