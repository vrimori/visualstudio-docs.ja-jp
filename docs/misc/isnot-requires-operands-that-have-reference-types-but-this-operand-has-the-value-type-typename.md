---
title: "&#39;IsNot&#39; には参照型を持つオペランドが必要ですが、このオペランドの値型は &#39;&lt;typename&gt;&#39; です。 | Microsoft Docs"
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
  - "bc31419"
  - "vbc31419"
helpviewer_keywords: 
  - "BC31419"
ms.assetid: c44d2936-8c07-443a-b320-ac2bfbc1e9ec
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;IsNot&#39; には参照型を持つオペランドが必要ですが、このオペランドの値型は &#39;&lt;typename&gt;&#39; です。
式で、値型のオペランドを少なくとも 1 つ持つ [IsNot Operator](/dotnet/visual-basic/language-reference/operators/isnot-operator) が使用されています。  
  
 `IsNot` 演算子は、2 つのオブジェクト参照が別のオブジェクトを参照しているかどうかを判断します。 この演算子は参照型のポインター値を比較するので、値型では意味がありません。  
  
 **エラー ID:** BC31419  
  
### このエラーを解決するには  
  
-   2 つの値型の値を比較する場合は、`=` または `<>` 比較演算子を使用します。  
  
-   2 つの参照型のポインターを比較する場合は、両方のオペランドのオブジェクト参照を使用していることを確認します。 参照変数や、[Me](http://msdn.microsoft.com/ja-jp/a65973c7-cf06-4547-9b25-9fba885525c2) キーワードのように参照変数のように動作する要素を使用できます。  
  
## 参照  
 [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [How to: Test Whether Two Objects Are the Same](../Topic/How%20to:%20Test%20Whether%20Two%20Objects%20Are%20the%20Same%20\(Visual%20Basic\).md)