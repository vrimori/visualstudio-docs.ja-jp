---
title: "Option Strict On では &#39;&lt;type1&gt;&#39; から &#39;&lt;type2&gt;&#39; への暗黙的な変換は許可されていません。Visual Basic 6.0 のコレクション型は .NET Framework のコレクション型と互換性がありません | Microsoft Docs"
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
  - "vbc30753"
  - "bc30753"
helpviewer_keywords: 
  - "BC30753"
ms.assetid: 7e1bb22e-a507-483e-bfd6-f3a43e24a232
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On では &#39;&lt;type1&gt;&#39; から &#39;&lt;type2&gt;&#39; への暗黙的な変換は許可されていません。Visual Basic 6.0 のコレクション型は .NET Framework のコレクション型と互換性がありません
`Option Strict On` では `<type1>` から `<type2>` への暗黙的な変換は許可されていません。Visual Basic 6.0 のコレクション型は [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のコレクション型と互換性がありません。  
  
 Visual Basic 6.0 で使用されるコレクション オブジェクトが、[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] で使用されているコレクション オブジェクトと異なります。  
  
 **エラー ID:** BC30753  
  
### このエラーを解決するには  
  
-   型変換のキーワードのいずれかを使用して、コレクション オブジェクトを明示的に変換します。[CType 関数](/dotnet/visual-basic/language-reference/functions/ctype-function) キーワードおよび [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator) キーワードでは、変換に失敗した場合、実行時例外がスローされます。 変換が失敗した場合、[TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator) キーワードは [Nothing](/dotnet/visual-basic/language-reference/nothing) を返します。  
  
## 参照  
 [CType 関数](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [NIB Visual Basic におけるコレクション](http://msdn.microsoft.com/ja-jp/8b2b7845-2251-4573-8dd3-c9f9c0a66a21)