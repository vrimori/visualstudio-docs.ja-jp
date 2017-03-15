---
title: "&#39;&lt;typeparametername&gt;&#39; は、クラス制約のない型パラメーターであるため、型 &#39;&lt;typeparametername&gt;&#39; の &#39;IsNot&#39; オペランドは、&#39;Nothing&#39; とのみ比較できます | Microsoft Docs"
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
  - "vbc32097"
  - "bc32097"
helpviewer_keywords: 
  - "BC32097"
ms.assetid: 50283a4b-70e3-4e59-9b9b-65e7cacf5ce1
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typeparametername&gt;&#39; は、クラス制約のない型パラメーターであるため、型 &#39;&lt;typeparametername&gt;&#39; の &#39;IsNot&#39; オペランドは、&#39;Nothing&#39; とのみ比較できます
型パラメーターが [IsNot Operator](/dotnet/visual-basic/language-reference/operators/isnot-operator) 演算子のオペランドとして使用されていますが、この型パラメーターの定義には [Class \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) キーワードがありません。また、制約リストにクラス名も指定されていません。  
  
 `IsNot` は 2 つの参照型を比較して、メモリ内で異なるオブジェクト インスタンスをポイントしているかどうかを判断します。 もう一方のオペランドが [Nothing](/dotnet/visual-basic/language-reference/nothing) でない限り、参照型でないオペランドを受け取ることはできません。  
  
 **エラー ID:** BC32097  
  
### このエラーを解決するには  
  
-   この型パラメーターに指定される型引数が常に参照型であることを要求できる場合は、`Class` キーワードを追加するか、その型パラメーターの制約リストにクラス名を指定します。  
  
-   この型パラメーターに指定される型引数が常に参照型であることを要求できない場合は、`IsNot` 式から型引数を削除してください。`IsNot` 演算子を使用して、他の参照型と比較することはできません。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)