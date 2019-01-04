---
title: CA1712:列挙型値を型名のプレフィックスにしません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4d91ac6b3312bda8daa88df29c94c6493f5e8546
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890077"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712:列挙型値を型名のプレフィックスにしません

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 列挙には、列挙体の型名で始まる名前を持つメンバーが含まれています。

## <a name="rule-description"></a>規則の説明
 列挙型メンバーの名前は、開発ツールが提供する型情報が予想されるため、型名でが付きますされません。

 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これには、新しいソフトウェア ライブラリを習得するために必要であり、ライブラリがマネージ コード開発の専門知識を持っている人によって開発されたという信頼を顧客が増加する時間が短縮されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、列挙型のメンバーから、型名のプレフィックスを削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、列挙型が不適切な名前であることを後に修正されたバージョンを示します。

 [!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
 [!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
 [!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>関連するルール
 [CA1711:識別子には、不適切なサフィックスはありません。](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027:FlagsAttribute で列挙をマークします。](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217:FlagsAttribute で列挙をマークしないでください。](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>関連項目

- <xref:System.Enum?displayProperty=fullName>