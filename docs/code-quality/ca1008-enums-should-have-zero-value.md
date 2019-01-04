---
title: CA1008:Enums は 0 値を含んでいなければなりません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b535424a391c91f57ce4a3d2edf997688989fdde
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53953382"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008:Enums は 0 値を含んでいなければなりません

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|改行しない - 追加するメッセージが表示されたら、 **None**非フラグ列挙体の値。 – 場合の名前を変更またはすべての列挙値を削除するように求められます。|

## <a name="cause"></a>原因

空の列挙定数を適用した<xref:System.FlagsAttribute?displayProperty=fullName>0; が、適用する列挙体の値を持つメンバーを一切定義しません<xref:System.FlagsAttribute>メンバーを定義します。 ゼロの値を持つが、その名が 'None'、または列挙体は、複数の値が 0 を定義します。メンバー。

## <a name="rule-description"></a>規則の説明

その他の値の型と同じように、初期化されていない列挙型の既定値には 0 です。 フラグの属性の列挙されるため、既定値は、列挙体の有効な値に 0 の値を持つメンバーを定義する必要があります。 必要に応じて、メンバーに名前を 'None' です。 それ以外の場合、最もよく使用されるメンバーに 0 を割り当てます。 既定では、宣言で、最初の列挙体メンバーの値が設定されていない場合、値は 0 です。

列挙型を持つ場合、<xref:System.FlagsAttribute>適用ゼロ値のメンバーの定義の名前には 'None' 列挙体の値が設定されていないことを示す必要があります。 使用とは異なり、他の目的は、ゼロ値のメンバーを使用して、<xref:System.FlagsAttribute>で AND とまたはビットごとの演算子がメンバーと役に立ちません。 これは、ため、その 1 つだけのメンバーに値 0 を割り当てる必要があります。 フラグの属性の列挙体の値が 0 である複数のメンバーが発生した場合`Enum.ToString()`が 0 でないメンバーが正しくない結果が返されます。

## <a name="how-to-fix-violations"></a>違反の修正方法

列挙体のフラグの属性には、この規則の違反を修正するには、0 以外の値を持つメンバーを定義します。これは、互換性に影響しない変更です。 値が 0 のメンバーを定義する列挙型フラグの属性、名前のメンバーを 'None' と 0 以外の値を持つその他のメンバーを削除します。これは、重大な変更です。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

以前にリリース済みフラグの属性の列挙型を除く、この規則による警告を抑制しないでください。

## <a name="example"></a>例

次の例は、ルールに適合する 2 つの列挙型と列挙体は、`BadTraceOptions`規則に違反しています。

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>関連するルール

- [CA2217:FlagsAttribute で列挙をマークしないでください。](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700:列挙値 'Reserved' という名前しない操作を行います](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA 1712:列挙型の値を型名のプレフィックスにしません](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA 1028:列挙ストレージは Int32 でなければなりません](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027:FlagsAttribute で列挙をマークします。](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>関連項目

- <xref:System.Enum?displayProperty=fullName>