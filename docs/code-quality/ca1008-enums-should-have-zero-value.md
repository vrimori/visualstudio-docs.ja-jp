---
title: 'CA1008: Enums は 0 値を含んでいなければなりません'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
ms.workload:
- multiple
ms.openlocfilehash: 4109bf7b455c7a77daa5b9d31b6fe1286cf69c77
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Enums は 0 値を含んでいなければなりません
|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|以外の区切りを追加するメッセージが表示されたら、 **None**フラグではない列挙値。– 場合名前か、すべての列挙値を削除するように求められます。|

## <a name="cause"></a>原因
 せず、適用した列挙体<xref:System.FlagsAttribute?displayProperty=fullName>0 ですまたは、適用した列挙体の値を持つメンバーを一切定義しません<xref:System.FlagsAttribute>メンバーを定義するゼロの値を持つが、その名前が 'None'、または列挙 0 の値を持つ複数の定義。メンバー。

## <a name="rule-description"></a>規則の説明
 その他の値の型と同じように、初期化されていない列挙型の既定値は 0 です。 フラグの属性の列挙をできるように、既定値は、列挙の有効な値に 0 の値を持つメンバーを定義する必要があります。 必要に応じて、メンバーに名前を 'None' です。 それ以外の場合、最も頻繁に使用するメンバーには 0 を割り当てます。 、既定では、宣言では、最初の列挙体メンバーの値が設定されていない場合、値がゼロであることを注意してください。

 列挙型を持つ場合、<xref:System.FlagsAttribute>適用値が 0 のメンバーを定義、名前が列挙体の値が設定されていないことを示すために ' None' にする必要があります。 それ以外の目的が使用するとは対照的では、ゼロ値のメンバーを使用して、<xref:System.FlagsAttribute>で AND とまたはビットごとの演算子がメンバーと役に立ちません。 つまり、その 1 つだけのメンバーに値 0 を割り当てる必要があります。 複数のメンバーがある場合、値が 0 発生フラグ属性の列挙にメモ`Enum.ToString()`が 0 でないメンバーを正しくない結果を返します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 列挙型のフラグの属性に対するこの規則の違反を修正するには、0 以外の値を持つメンバーを定義しますこれは、互換性に影響する変更点以外です。 フラグ属性列挙型の値が 0 のメンバーを定義する、名前のメンバーを 'None' とゼロ以外の値を持つ他のメンバーを削除します。これは、互換性に影響する変更点です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 以前にリリース済みフラグ属性の列挙体を除く、この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例は、ルールに適合する 2 つの列挙型、および列挙体、`BadTraceOptions`規則に違反しています。

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>関連規則
 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: enum 値に 'Reserved' という名前を指定しません](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: enum 値を型名のプレフィックスにしません](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: 列挙ストレージは Int32 でなければなりません](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>関連項目
 <xref:System.Enum?displayProperty=fullName>