---
title: CA2224:オーバーロードする演算子 equals で Equals をオーバーライドします
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: af2b1af90620fa595d85f7c26d7e5e2c96041dfc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826089"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224:オーバーロードする演算子 equals で Equals をオーバーライドします

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

パブリック型は、等値演算子を実装しますが、オーバーライドしない<xref:System.Object.Equals%2A?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明

構文上便利な方法の機能にアクセスするものでは、等値演算子、<xref:System.Object.Equals%2A>メソッド。 そのロジックがの場合と同じである必要があります、等値演算子を実装する場合<xref:System.Object.Equals%2A>します。

C# コンパイラは、コードにこの規則に違反している場合に警告を発行します。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには、する必要があります、等値演算子の実装を削除または上書き<xref:System.Object.Equals%2A>し、2 つのメソッドが同じ値を返します。 実装を提供することで、違反を修正するには、等値演算子は、一貫性のない動作を導入していない場合、<xref:System.Object.Equals%2A>を呼び出す、<xref:System.Object.Equals%2A>基底クラス メソッド。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

等値演算子は、継承された実装のと同じ値を返す場合、この規則による警告を抑制するのには安全では<xref:System.Object.Equals%2A>します。 この記事の例には、この規則による警告を安全に抑制する型が含まれます。

## <a name="examples-of-inconsistent-equality-definitions"></a>一貫性のない等価性の定義の例

次の例では、等値の一貫性のない定義を持つ型を示します。 `BadPoint` 等値の意味を等値演算子のカスタム実装を提供することで変更しますが、オーバーライドしない<xref:System.Object.Equals%2A>と同様に動作できるようにします。

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

次のコードの動作をテストする`BadPoint`します。

[!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

この例を実行すると、次の出力が生成されます。

```txt
a =  ([0] 1,1) and b = ([1] 2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? No
b == bcopy ? Yes
```

次の例では、技術的には、この規則に違反していますが、一貫性のある方法で動作しない型を示します。

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

次のコードの動作をテストする`GoodPoint`します。

[!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

この例を実行すると、次の出力が生成されます。

```txt
a =  (1,1) and b = (2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? Yes
b == bcopy ? Yes
```

## <a name="class-example"></a>クラスの例

次の例では、この規則に違反するためのクラス (参照型) を示します。

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

次の例では、オーバーライドすることで、違反を修正する<xref:System.Object.Equals%2A?displayProperty=fullName>します。

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>構造の例

次の例では、この規則に違反する構造体 (値型) を示します。

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

次の例では、オーバーライドすることで、違反を修正する<xref:System.ValueType.Equals%2A?displayProperty=fullName>します。

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>関連するルール

[CA1046:参照型で、演算子 equals をオーバー ロードしません。](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225:演算子のオーバー ロード名前付けされた代替](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226:演算子は対称型オーバー ロードである必要があります。](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218:Equals をオーバーライドの GetHashCode をオーバーライドします。](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)