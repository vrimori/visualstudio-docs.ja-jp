---
title: "CA1046: 参照型で、演算子 equals をオーバーロードしないでください | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
  - "CA1046"
helpviewer_keywords: 
  - "CA1046"
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1046: 参照型で、演算子 equals をオーバーロードしないでください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリックの参照型または入れ子になったパブリックの参照型が、等値演算子をオーバーロードしています。  
  
## 規則の説明  
 参照型の場合、等値演算子は既定の実装でほぼ問題がありません。  既定で、2 つの参照が等値と見なされるのは、同じオブジェクトを参照する場合のみです。  
  
## 違反の修正方法  
 この規則違反を修正するには、等値演算子の実装を削除します。  
  
## 警告を抑制する状況  
 参照型が組み込みの値型のように動作する場合は、この規則による警告を抑制しても安全です。  型のインスタンスで加算または減算を実行する意味がある場合、多くは、等値演算子を実装して警告を抑制することが適切です。  
  
## 使用例  
 2 つの参照を比較するときの既定の動作を次の例に示します。  
  
 [!code-cs[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## 使用例  
 次のアプリケーションでは、いくつかの参照を比較しています。  
  
 [!code-cs[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **a \= new \(2,2\) and b \= new \(2,2\) are equal?  No**  
**c and a are equal?  Yes**  
**b and a are \=\= ?  No**  
**c and a are \=\= ?  Yes**    
## 関連規則  
 [CA1013: オーバーロードする加算および減算で、演算子 equals をオーバーロードします](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## 参照  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [等値演算子](../Topic/Equality%20Operators.md)