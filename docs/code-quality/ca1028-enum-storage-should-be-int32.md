---
title: 'CA1028: 列挙ストレージは Int32 でなければなりません'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e27b93e354230e88e4e76ba4836b88eac7fa4c7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: 列挙ストレージは Int32 でなければなりません
|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック列挙型の基になる型がありません<xref:System.Int32?displayProperty=fullName>です。

## <a name="rule-description"></a>規則の説明
 列挙型は、関連する名前付き定数が複数定義された値型です。 既定では、<xref:System.Int32?displayProperty=fullName>定数の値を格納するデータ型を使用します。 できます、この変更の種類を基になる場合でもはないために必要なまたは推奨されるほとんどのシナリオです。 も小さいデータ型を使用して大幅なパフォーマンスの向上が実現されていないことに注意してください<xref:System.Int32>です。 既定のデータ型を使用できない場合は場合、共通言語システム (CLS) のいずれかを使用する必要があります-準拠の整数型<xref:System.Byte>、 <xref:System.Int16>、 <xref:System.Int32>、または<xref:System.Int64>で列挙体のすべての値を表すことがあるかどうかを確認するにはCLS 準拠のプログラミング言語です。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、サイズや互換性の問題がない限り使用<xref:System.Int32>です。 場合、<xref:System.Int32>が小さすぎて値を保持するには、使用<xref:System.Int64>です。 旧バージョンとの互換性は、小さいデータ型を必要とする場合を使用して<xref:System.Byte>または<xref:System.Int16>です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 旧バージョンと互換性の問題に必要な場合にのみ、この規則による警告を抑制します。 アプリケーションでは、通常この規則に準拠しないには、問題は発生しません。 ライブラリでは、言語の相互運用性が必要なこの規則に準拠しない可能性がありますに悪影響がします。

## <a name="example-of-a-violation"></a>違反の例

### <a name="description"></a>説明
 次の例では、推奨される基になるデータ型を使用して 2 つの列挙型を示します。

### <a name="code"></a>コード
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>修正する方法の例

### <a name="description"></a>説明
 次の例では、前の違反を修正する基になるデータ型を変更することによって<xref:System.Int32>です。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>関連規則
 [CA1008: Enums は 0 値を含んでいなければなりません](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: enum 値に 'Reserved' という名前を指定しません](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: enum 値を型名のプレフィックスにしません](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>関連項目
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName> <xref:System.Int32?displayProperty=fullName> <xref:System.Int64?displayProperty=fullName>