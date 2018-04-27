---
title: 'CA2217: enums を FlagsAttribute に設定しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12cc5f9fc58ac533d118b693587cf807f44b288f
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: enums を FlagsAttribute に設定しません

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

マークされている外部から参照できる列挙<xref:System.FlagsAttribute>、および 1 つまたは 2 つ、またはその他の組み合わせの累乗ではない値がその列挙型で値を定義します。

## <a name="rule-description"></a>規則の説明

列挙型である必要があります<xref:System.FlagsAttribute>定義された値の列挙で定義された各値が 2 つの組み合わせの電源である場合にのみ存在します。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を解決するには、削除<xref:System.FlagsAttribute>列挙体からです。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。

## <a name="example-that-should-not-have-the-attribute"></a>属性のない例

次の例では、列挙型、 `Color`3 の値を格納します。 3 は、2、または定義済みの値のいずれかの組み合わせの電源ではありません。 `Color`で列挙型をマークすることはできません<xref:System.FlagsAttribute>です。

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example-that-should-have-the-attribute"></a>属性を持つ必要がありますの例

次の例では、列挙型、`Days`でマークされているための要件を満たしている<xref:System.FlagsAttribute>です。

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>関連規則

[CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>関連項目

- <xref:System.FlagsAttribute?displayProperty=fullName>
