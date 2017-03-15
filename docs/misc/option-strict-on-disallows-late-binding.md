---
title: "Option Strict On では、遅延バインディングを使用できません | Microsoft Docs"
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
  - "bc30574"
  - "vbc30574"
helpviewer_keywords: 
  - "BC30574"
ms.assetid: 9da4b826-2e12-4a5d-9e17-762b0b68fc9b
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On では、遅延バインディングを使用できません
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では、任意のデータ型を他の任意のデータ型に暗黙的に変換できます。 ただし、あるデータ型の値を精度が低いデータ型または容量の小さいデータ型に変換すると、データ損失が発生する可能性があります。`Option Strict On` を使用すると、このような型の変換についてコンパイル時に通知が送信されるため、変換を回避できます。 遅延バインディングとともに `Option Strict On` を使用することはできません。  
  
 遅延バインディングを使用し、`Option Strict` を `On` に設定した場合にこのエラーが発生するコード例を次に示します。  
  
 [!CODE [VbVbalrOptionStrictError#1](VbVbalrOptionStrictError#1)]  
  
 **エラー ID:** BC30574  
  
### このエラーを解決するには  
  
-   次の例のように、明示的な型を使用するようにオブジェクト宣言を変更します。  
  
     [!CODE [VbVbalrOptionStrictError#2](VbVbalrOptionStrictError#2)]  
  
 または  
  
-   次の例のように、明示的な型を指定するように遅延バインディング式を変更します。  
  
     [!CODE [VbVbalrOptionStrictError#3](VbVbalrOptionStrictError#3)]  
  
 または  
  
-   次の例のように、コンパイラで特定の型を推論するようにします。  
  
     [!CODE [VbVbalrOptionStrictError#4](VbVbalrOptionStrictError#4)]  
  
 または  
  
-   `On` という単語を削除するか、`Off` を明示的に指定して `Option Strict` をオフにします。  
  
## 参照  
 [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)