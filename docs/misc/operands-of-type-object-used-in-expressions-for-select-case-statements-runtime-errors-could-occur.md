---
title: "&#39;Select&#39;、&#39;Case&#39; ステートメントの式でオブジェクト型のオペランドが使用されています。ランタイム エラーが発生する可能性があります | Microsoft Docs"
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
  - "vbc42036"
  - "bc42036"
helpviewer_keywords: 
  - "BC42036"
ms.assetid: f11e9c9f-aa66-4eb1-8f49-abf713bef885
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Select&#39;、&#39;Case&#39; ステートメントの式でオブジェクト型のオペランドが使用されています。ランタイム エラーが発生する可能性があります
`Select`...`Case` コンストラクションは、[Object Data Type](/dotnet/visual-basic/language-reference/data-types/object-data-type) の 1 つまたは複数の式を使用します。  
  
 変数または式が `Object` と評価される場合、コンパイラは*遅延バインディング*を実行する必要があり、これによって実行時に余分な処理が発生します。 また、アプリケーションで実行時エラーが発生する可能性があります。 たとえば、<xref:System.Windows.Forms.Form> を `Object` 変数に割り当て、数値と比較しようとした場合、Visual Basic は <xref:System.Windows.Forms.Form> オブジェクトを数値に変換できないため、ランタイムは <xref:System.InvalidCastException> をスローします。  
  
 `Select`...`Case` コンストラクション内の式は、すべて同じデータ型であるか、または相互に変換できる、密接に関連するデータ型である必要があります。 これは、各 `Case` ステートメントが、`Select`...`Case` コンストラクションのベースとなっているテスト式に対して、1 つ以上の値を比較するからです。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42036  
  
### このエラーを解決するには  
  
-   可能であれば、比較演算子の定義されているデータ型にすべての式が評価されるように調整します。  
  
## 参照  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Arithmetic Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators)   
 [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)