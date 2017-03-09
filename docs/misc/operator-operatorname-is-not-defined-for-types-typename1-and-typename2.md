---
title: "型 &lt;typename1&gt;&#39; および &#39;&lt;typename2&gt;&#39; に対して演算子 &#39;&lt;operatorname&gt;&#39; が定義されていません。 | Microsoft Docs"
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
  - "vbc31080"
  - "bc31080"
helpviewer_keywords: 
  - "BC31080"
ms.assetid: d2f77450-2bf2-4b1e-b95f-dbc7878f2777
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &lt;typename1&gt;&#39; および &#39;&lt;typename2&gt;&#39; に対して演算子 &#39;&lt;operatorname&gt;&#39; が定義されていません。
型 \<typename1\>' および '\<typename2\>' に対して演算子 '\<operatorname\>' が定義されていません。 'Is' 演算子を使用すると、2 つの参照型を比較できます。  
  
 指定した型に対して不適切な方法で、演算子を使用しようとしました。 このエラーは、`Is` 演算子ではなく "\=" 演算子を使用して、2 つのオブジェクトを比較すると発生する可能性があります。  
  
 **エラー ID:** BC31080  
  
### このエラーを解決するには  
  
1.  `Is` 演算子を使用して、2 つの参照型を比較します。  
  
2.  `Not` 演算子を `Is` 演算子と組み合わせて使用して、非等値を表します。 例:  
  
     [!code-vb[VbVbalrOOP#89](../misc/codesnippet/VisualBasic/operator-operatorname-is-not-defined-for-types-typename1-and-typename2_1.vb)]  
  
## 参照  
 [Is Operator](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [\= Operator](/dotnet/visual-basic/language-reference/operators/assignment-operator)   
 [Not Operator](/dotnet/visual-basic/language-reference/operators/not-operator)