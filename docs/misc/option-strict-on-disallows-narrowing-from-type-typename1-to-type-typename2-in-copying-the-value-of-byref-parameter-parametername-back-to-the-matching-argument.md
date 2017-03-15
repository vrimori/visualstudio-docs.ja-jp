---
title: "Option Strict On では、&#39;ByRef&#39; パラメーター &lt;parametername&gt;&#39; の値を、一致する引数に戻してコピーする際に、型 &#39;&lt;typename1&gt;&#39; から型 &#39;&lt;typename2&gt;&#39; に縮小変換することはできません | Microsoft Docs"
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
  - "bc32029"
  - "vbc32029"
helpviewer_keywords: 
  - "BC32029"
ms.assetid: fc9ae5d2-b506-47cf-a50c-116fda5ed206
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On では、&#39;ByRef&#39; パラメーター &lt;parametername&gt;&#39; の値を、一致する引数に戻してコピーする際に、型 &#39;&lt;typename1&gt;&#39; から型 &#39;&lt;typename2&gt;&#39; に縮小変換することはできません
プロシージャ呼び出しは、`ByRef` 引数に、引数の宣言タイプに拡大変換されるデータ型を指定し、`Option Strict` は `On` です。 拡大変換はプロシージャに引数が渡されるときに使用できますが、プロシージャが呼び出し元のコード内の可変引数の内容を変更するとき、逆変換は縮小になります。`Option Strict On` では縮小変換は許可されません。  
  
 **エラー ID:** BC32029  
  
### このエラーを解決するには  
  
-   プロシージャ呼び出し内の各 `ByRef` 引数に、宣言された型と同じデータ型を指定するか、または `Option Strict Off` に切り替えます。  
  
## 参照  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)