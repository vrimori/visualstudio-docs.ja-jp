---
title: "Ca 2231: ValueType.Equals のオーバーライドで equals をオーバー ロードされた演算子 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9ee207eb3e5c4babb5bcb9f7d88f9afd3908a3c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします
|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|CheckId|CA2231|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 値の型のオーバーライド<xref:System.Object.Equals%2A?displayProperty=fullName>等値演算子を実装しません。  
  
## <a name="rule-description"></a>規則の説明  
 ほとんどのプログラミング言語では、値型の等値演算子 (= =) の既定の実装はありません。 使用するプログラミング言語では、演算子のオーバー ロードをサポートする場合は、等値演算子を実装することを検討してください。 その動作をするのと同じにする必要があります<xref:System.Object.Equals%2A>です。  
  
 等値演算子のオーバー ロードされた実装では、既定の等値演算子を使用できません。 こうと、スタック オーバーフローが発生します。 等値演算子を実装するのには、実装で、Object.Equals メソッドを使用します。 例:  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```csharp  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、等値演算子を実装します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告を抑制しても安全です。ただし、可能であれば、等値演算子を指定することをお勧めします。  
  
## <a name="example"></a>例  
 次の例では、この規則に違反する型を定義します。  
  
 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1046: 参照型で、演算子 equals をオーバーロードしないでください](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: 演算子オーバーロードには名前付けされた代替が存在します](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: 演算子は対称型オーバーロードを含まなければなりません](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: オーバーライドする Equals で GetHashCode をオーバーライドします](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## <a name="see-also"></a>参照  
 <xref:System.Object.Equals%2A?displayProperty=fullName>