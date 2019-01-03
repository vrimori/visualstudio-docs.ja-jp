---
title: CA2218:オーバーライドする Equals で GetHashCode をオーバーライドします
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c57ebb8f808ba98acb673ad3fbbc3ba78bcdc3ac
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860872"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218:オーバーライドする Equals で GetHashCode をオーバーライドします

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 パブリック型のオーバーライド<xref:System.Object.Equals%2A?displayProperty=fullName>がオーバーライドしません<xref:System.Object.GetHashCode%2A?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 <xref:System.Object.GetHashCode%2A> ハッシュ アルゴリズムやハッシュ テーブルなどのデータ構造に適していますが、現在のインスタンスに基づいて、値を返します。 同じ種類し、が等しい 2 つのオブジェクトには、次の型のインスタンスが正しく動作する同じハッシュ コードを返す必要があります。

- <xref:System.Collections.Hashtable?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

- 実装する型 <xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、実装を提供<xref:System.Object.GetHashCode%2A>します。 同じ型のオブジェクトのペアの場合、実装が同じ値を返すことを確認する必要がありますの実装<xref:System.Object.Equals%2A>返します`true`ペアを指定します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="class-example"></a>クラスの例

### <a name="description"></a>説明
 次の例では、この規則に違反するためのクラス (参照型) を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]

### <a name="comments"></a>コメント
 次の例では、オーバーライドすることで、違反を修正する<xref:System.Object.GetHashCode>します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]

## <a name="structure-example"></a>構造の例

### <a name="description"></a>説明
 次の例では、この規則に違反する構造体 (値型) を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]

### <a name="comments"></a>コメント
 次の例では、オーバーライドすることで、違反を修正する<xref:System.Object.GetHashCode>します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]

## <a name="related-rules"></a>関連するルール
 [CA1046:参照型で、演算子 equals をオーバー ロードしません。](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225:演算子のオーバー ロード名前付けされた代替](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226:演算子は対称型オーバー ロードである必要があります。](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224:オーバー ロードする演算子 equals で equals をオーバーライド](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>関連項目

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [等値演算子](/dotnet/standard/design-guidelines/equality-operators)