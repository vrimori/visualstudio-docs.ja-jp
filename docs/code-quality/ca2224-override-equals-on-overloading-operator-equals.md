---
title: 'CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8836644e109e37855aa79dc67b461591b273786
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921513"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします
|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 パブリック型は、等値演算子を実装しますが、オーバーライドしません<xref:System.Object.Equals%2A?displayProperty=fullName>です。

## <a name="rule-description"></a>規則の説明
 等値演算子は、の機能にアクセスする構文的に便利な手段をするものでは、<xref:System.Object.Equals%2A>メソッドです。 そのロジックがの場合と同じである必要があります、等値演算子を実装する場合<xref:System.Object.Equals%2A>です。

 C# コンパイラは、コードには、この規則が違反している場合に警告を発行します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正する必要がありますか、等値演算子の実装を削除または上書きする<xref:System.Object.Equals%2A>し、2 つのメソッドが同じ値を返します。 実装を提供することで、違反を修正するには、等値演算子は、一貫性のない動作を導入していない場合、<xref:System.Object.Equals%2A>を呼び出す、<xref:System.Object.Equals%2A>基底クラスのメソッドです。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 等値演算子は、継承した実装と同じ値を返す場合は、この規則による警告を抑制するのには安全では<xref:System.Object.Equals%2A>します。 例」のセクションには、この規則による警告を抑制することが安全にする型が含まれています。

## <a name="examples-of-inconsistent-equality-definitions"></a>矛盾した等値の定義の例

### <a name="description"></a>説明
 次の例では、等値の一貫性のない定義を持つ型を示します。 `BadPoint` 等値演算子のカスタム実装を提供することで等値の意味を変更し、オーバーライドしません<xref:System.Object.Equals%2A>同じように動作できるようにします。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

## <a name="example"></a>例
 次のコードの動作をテストする`BadPoint`です。

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

 この例を実行すると、次の出力が生成されます。

 **= ([0] 1, 1) と b ([1] 2, 2) を = が等しいか?いいえ**
**b を = = しますか?いいえ**
**a1 と等しいか?[はい]**
**a1 = =、ですか?[はい]**
**b と間が等しいか?いいえ**
**b 間の = = しますか?うん**
## <a name="example"></a>例
 次の例では、技術的には、この規則に違反していますが、一貫性のある方法で動作しない型を示します。

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

## <a name="example"></a>例
 次のコードの動作をテストする`GoodPoint`です。

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

 この例を実行すると、次の出力が生成されます。

 **= (1, 1) と b = (2, 2) が等しいか?いいえ**
**b を = = しますか?いいえ**
**a1 と等しいか?[はい]**
**a1 = =、ですか?[はい]**
**b と間が等しいか?[はい]**
**b 間の = = しますか?うん**
## <a name="class-example"></a>クラスの例

### <a name="description"></a>説明
 次の例では、この規則に違反するためのクラス (参照型) を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

## <a name="example"></a>例
 次の例は、オーバーライドすることで違反を修正<xref:System.Object.Equals%2A?displayProperty=fullName>です。

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>構造の例

### <a name="description"></a>説明
 次の例では、この規則に違反する構造体 (値型) を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

## <a name="example"></a>例
 次の例は、オーバーライドすることで違反を修正<xref:System.ValueType.Equals%2A?displayProperty=fullName>です。

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>関連規則
 [CA1046: 参照型で、演算子 equals をオーバーロードしないでください](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: 演算子オーバーロードには名前付けされた代替が存在します](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: 演算子は対称型オーバーロードを含まなければなりません](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: オーバーライドする Equals で GetHashCode をオーバーライドします](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)