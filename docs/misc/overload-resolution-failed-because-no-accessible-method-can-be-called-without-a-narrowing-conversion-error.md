---
title: "縮小変換しないで呼び出される、アクセス可能な &#39;&lt;method&gt;&#39; がないため、オーバーロードの解決に失敗しました: &lt;error&gt; | Microsoft Docs"
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
  - "vbc30519"
  - "bc30519"
helpviewer_keywords: 
  - "BC30519"
ms.assetid: 3b3e724d-6fad-4146-b47d-6525493b2fa8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 縮小変換しないで呼び出される、アクセス可能な &#39;&lt;method&gt;&#39; がないため、オーバーロードの解決に失敗しました: &lt;error&gt;
オーバーロードされたメソッドを呼び出しましたが、コンパイラで、縮小変換せずに呼び出すことのできるメソッドを検出できません。 縮小変換により、有効値の一部を正確に保持できない可能性のあるデータ型に値が変更されます。  
  
 **エラー ID:** BC30519  
  
### このエラーを解決するには  
  
-   `Option Strict Off` を指定します。  
  
## 参照  
 [Overloaded Properties and Methods](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)