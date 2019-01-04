---
title: CA2217:列挙型を FlagsAttribute に設定しません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: d8afe63de8630b3fa7466e8c0784c26ba00bb1ba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852480"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217:列挙型を FlagsAttribute に設定しません

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

外部から参照できる列挙体が付いた<xref:System.FlagsAttribute>とが 1 つまたは 2 つ、またはその他の組み合わせの累乗でない多くの値が列挙型で値を定義します。

## <a name="rule-description"></a>規則の説明

列挙体である必要があります<xref:System.FlagsAttribute>列挙で定義されている各値の組み合わせまたは 2 の累乗が場合にのみ存在する値を定義します。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには、削除<xref:System.FlagsAttribute>列挙体から。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。

## <a name="example-that-should-not-have-the-attribute"></a>属性のない例

次の例では、列挙体は、 `Color`3 の値を格納します。 3 は、2、または定義済みの値のいずれかの組み合わせのべき乗ではありません。 `Color`で列挙型をマークすることはできません<xref:System.FlagsAttribute>します。

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example-that-should-have-the-attribute"></a>属性が持つべき例

次の例では、列挙体は、`Days`でマークされているの要件を満たしている<xref:System.FlagsAttribute>します。

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>関連するルール

[CA1027:FlagsAttribute で列挙をマークします。](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>関連項目

- <xref:System.FlagsAttribute?displayProperty=fullName>
