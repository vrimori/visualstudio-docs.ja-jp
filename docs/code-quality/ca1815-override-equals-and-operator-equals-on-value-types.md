---
title: "Ca 1815: 上書き equals および operator equals を値型で |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 927e13266bf308096592fb5714e1247f4b596ca8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: equals および operator equals を値型でオーバーライドします
|||  
|-|-|  
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|  
|CheckId|CA1815|  
|カテゴリ|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 パブリックの値の型をオーバーライドしません<xref:System.Object.Equals%2A?displayProperty=fullName>、等値演算子 (= =) を実装していませんか。 このルールでは、列挙型はチェックされません。  
  
## <a name="rule-description"></a>規則の説明  
 値型、継承した実装の<xref:System.Object.Equals%2A>Reflection ライブラリを使用し、すべてのフィールドの内容を比較します。 Reflection は計算コストが高いため、場合によってはすべてのフィールドで等値性を比較する必要はありません。 値の型を実装する必要があります比較または並べ替えのインスタンスにユーザーを想定してハッシュ テーブル キーとして使用するか、<xref:System.Object.Equals%2A>です。 お使いのプログラミング言語が演算子のオーバーロードに対応している場合、等値演算子と非等値演算子も実装してください。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、実装を提供<xref:System.Object.Equals%2A>です。 場合は、等値演算子を実装することができます。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 値の型のインスタンスは互いに比較しない場合は、この規則による警告を抑制するのには安全です。  
  
## <a name="example-of-a-violation"></a>違反の例  
  
### <a name="description"></a>説明  
 次の例では、この規則に違反する構造体 (値型) を示します。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]  
  
## <a name="example-of-how-to-fix"></a>修正する方法の例  
  
### <a name="description"></a>説明  
 次の例は、オーバーライドすることで以前の違反を修正<xref:System.ValueType.Equals%2A?displayProperty=fullName>と実装の等値演算子 (= =、! =)。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
 [CA2226: 演算子は対称型オーバーロードを含まなければなりません](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
## <a name="see-also"></a>参照  
 <xref:System.Object.Equals%2A?displayProperty=fullName>