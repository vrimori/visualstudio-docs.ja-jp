---
title: 'CA1712: enum 値を型名のプレフィックスにしません'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b6d8a5ebba4f746c7418fcfb28a61d98949441e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: enum 値を型名のプレフィックスにしません
|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 列挙には、列挙体の型名から始まる名前を持つメンバーが含まれています。

## <a name="rule-description"></a>規則の説明
 列挙体メンバーの名前がプレフィックスが付いていない型名の種類の情報が予想される、開発ツールによって提供されるためです。

 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 新しいソフトウェア ライブラリを習得するために必要であり、ライブラリは、マネージ コード開発の専門知識を持つユーザーによって開発された顧客の信頼度が高まりますある時間を短縮します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、列挙型のメンバーから、型名のプレフィックスを削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、修正の後に不適切な名前列挙型を示します。

 [!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
 [!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
 [!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>関連規則
 [CA1711: 識別子は、不適切なサフィックスを含むことはできません](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>関連項目
 <xref:System.Enum?displayProperty=fullName>