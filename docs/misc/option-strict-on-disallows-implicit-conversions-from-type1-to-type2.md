---
title: "Option Strict On では、&#39;&lt;type1&gt;&#39; から &#39;&lt;type2&gt;&#39; への暗黙的な変換はできません | Microsoft Docs"
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
  - "bc30512"
  - "vbc30512"
helpviewer_keywords: 
  - "BC30512"
ms.assetid: b9756d48-05fa-4027-8a80-b4a0ef92099d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On では、&#39;&lt;type1&gt;&#39; から &#39;&lt;type2&gt;&#39; への暗黙的な変換はできません
`Long` から `Integer` への変換のように、値を格納できなくなる可能性がある別の型への型変換を行おうとしましたが、型チェック スイッチ \([Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)\) は `On` に設定されています。  
  
 この種の変換は*縮小変換*と呼ばれ、実行時の失敗の原因になる場合があります。 このため、`Option Strict On` では暗黙的な縮小変換が禁止されています。  
  
 **エラー ID:** BC30512  
  
### このエラーを解決するには  
  
1.  `<type1>` から `<type2>` への何らかの型変換が存在するかどうかを判断します。 共に [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の基本型であるか、共にクラス インスタンスである場合、「[Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)」の表を参照して通常は判断できます。  
  
2.  `<type1>` から `<type2>` への縮小変換のみが存在する場合は、明示的なキャストを使用する必要があります。[CType 関数](/dotnet/visual-basic/language-reference/functions/ctype-function) キーワードおよび [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator) キーワードでは、変換に失敗した場合、実行時例外がスローされます。[TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator) キーワードは参照型のみに適用でき、変換が失敗した場合は [Nothing](/dotnet/visual-basic/language-reference/nothing) を返します。  
  
3.  縮小変換が存在し、プログラムがランタイム エラーを許容できる場合、または、ランタイム エラーは発生しないと確信している場合は、ソース コードの先頭に `Option Strict Off` を指定できます。 それでも、予期しない結果や、プログラムの早期終了を避けるために、変換を [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) ブロックで囲む必要があります。  
  
4.  `<type1>` から `<type2>` への変換が存在しない場合は、プログラム ロジックを再評価する必要があります。 予測される `<type1>` の値に対応して `<type2>` に値を代入するコードを記述できます。  
  
5.  `<type1>` から `<type2>` への変換が存在せず、型の 1 つが自分で定義したクラスまたは構造体である場合は、一方の型から他方の型に、またはその逆に型を変換できる変換演算子を定義できます。 詳細については、「[How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)」を参照してください。  
  
6.  一般的なガイドラインとしては、`Catch` ブロックでエラーをトラップして効率的に処理できるのでない限り、どのような場合であれ縮小変換は使用しないようにお勧めします。  
  
## 参照  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [CType 関数](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)