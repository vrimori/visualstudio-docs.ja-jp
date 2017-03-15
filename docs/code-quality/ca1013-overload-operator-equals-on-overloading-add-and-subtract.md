---
title: "CA1013: オーバーロードする加算および減算で、演算子 equals をオーバーロードします | Microsoft Docs"
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
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
helpviewer_keywords: 
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1013: オーバーロードする加算および減算で、演算子 equals をオーバーロードします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|  
|CheckId|CA1013|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 パブリック型またはプロテクト型で、等値演算子を実装しないまま、加算演算子または減算演算子を実装しています。  
  
## 規則の説明  
 加算や減算などの演算を使用して型のインスタンスを結合できる場合、同じ構成値を持つ任意の 2 つのインスタンスについて `true` を返すには、ほぼ常に等値性を定義する必要があります。  
  
 等値演算子がオーバーロードされた実装では、既定の等値演算子は使用できません。  使用すると、スタック オーバーフローが発生します。  等値演算子を実装するには、Object.Equals メソッドを使用します。  次の例を参照してください。  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```c#  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## 違反の修正方法  
 この規則違反を修正するには、等値演算子を実装して、数学的に加算演算子および減算演算子と合わせます。  
  
## 警告を抑制する状況  
 既定の実装の等値演算子でも型が正しく機能する場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 この規則に違反する型 \(`BadAddableType`\) の定義を次の例に示します。  この型では、等値演算子を実装し、同じフィールドを持つ任意の 2 つのインスタンスについて、等値性の `true` をテストする必要があります。  型 `GoodAddableType` は、正しい実装例です。  この型では、非等値演算子も実装し、<xref:System.Object.Equals%2A> をオーバーライドしている点に注意してください。これは他の規則に適合するためです。  実際に使用する場合、<xref:System.Object.GetHashCode%2A> も実装します。  
  
 [!code-cs[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]  
  
## 使用例  
 次の例では、上記で定義した型のインスタンスを使用して等値性をテストしています。これで、等値演算子の既定の動作と修正後の動作がわかります。  
  
 [!code-cs[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **Bad type:  {2,2} {2,2} are equal?  No**  
**Good type: {3,3} {3,3} are equal?  Yes**  
**Good type: {3,3} {3,3} are \=\= ?Yes**  
**Bad type:  {2,2} {9,9} are equal?  No**  
**Good type: {3,3} {9,9} are \=\= ?No**    
## 参照  
 [等値演算子](../Topic/Equality%20Operators.md)