---
title: "CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
  - "CA2231"
  - "OverrideOperatorEqualsOnOverridingValueTypeEquals"
helpviewer_keywords: 
  - "CA2231"
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|CheckId|CA2231|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 値型は <xref:System.Object.Equals%2A?displayProperty=fullName> をオーバーロードしますが、等値演算子は実装していません。  
  
## 規則の説明  
 ほとんどのプログラミング言語では、値型に対する等値演算子 \(\=\=\) の既定の実装がありません。  プログラミング言語で演算子のオーバーロードをサポートしている場合、等値演算子の実装を考慮してください。  等値演算子の動作は、<xref:System.Object.Equals%2A> と同様です。  
  
 等値演算子がオーバーロードされた実装では、既定の等値演算子は使用できません。  使用すると、スタック オーバーフローが発生します。  等値演算子を実装するには、Object.Equals メソッドを使用します。  たとえば、次のようになります。  
  
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
 この規則違反を修正するには、等値演算子を実装します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しても安全ですが、可能であれば等値演算子を実装することをお勧めします。  
  
## 使用例  
 この規則に違反する型の定義を次の例に示します。  
  
 [!CODE [FxCop.Usage.EqualsGetHashCode#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode#1)]  
  
## 関連規則  
 [CA1046: 参照型で、演算子 equals をオーバーロードしないでください](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: 演算子オーバーロードには名前付けされた代替が存在します](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226: 演算子は対称型オーバーロードを含まなければなりません](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: オーバーライドする Equals で GetHashCode をオーバーライドします](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## 参照  
 <xref:System.Object.Equals%2A?displayProperty=fullName>