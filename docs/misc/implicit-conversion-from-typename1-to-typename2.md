---
title: "&#39;&lt;typename1&gt;&#39; から &#39;&lt;typename2&gt;&#39; への暗黙的な変換 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42016"
  - "BC42016"
helpviewer_keywords: 
  - "BC42016"
ms.assetid: 7dabaab0-8258-4c17-927f-28e61f50bd3a
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename1&gt;&#39; から &#39;&lt;typename2&gt;&#39; への暗黙的な変換
式または代入ステートメントで、あるデータ型の値が取得され、別の型に変換されます。 変換キーワードが使用されていないため、この変換は *暗黙的* です。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42016  
  
### このエラーを解決するには  
  
-   可能な場合は、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] による変換が必要ないように、同じデータ型の値を使用します。  
  
-   変換が *明示的* になるように、`CType` またはその他の変換キーワードのいずれかを使用します。  
  
## 参照  
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)