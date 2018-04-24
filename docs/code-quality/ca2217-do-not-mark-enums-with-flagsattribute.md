---
title: 'CA2217: enums を FlagsAttribute に設定しません'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1aaa080aaa238f15cbcedefd9302d23758948d77
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: enums を FlagsAttribute に設定しません
|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 マークされている外部から参照できる列挙<xref:System.FlagsAttribute>と 1 つまたは 2 つ、またはその他の組み合わせの累乗ではない値がその列挙型で値を定義します。

## <a name="rule-description"></a>規則の説明
 列挙型である必要があります<xref:System.FlagsAttribute>列挙で定義された各値は、2 の累乗またはの組み合わせには、値が定義されている場合にのみ存在します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するには、削除<xref:System.FlagsAttribute>列挙体からです。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、列挙、色、値は 3 に含まれているがどちらも 2 の累乗も定義されている値のいずれかの組み合わせを示します。 マークしないで Color 列挙型、<xref:System.FlagsAttribute>です。

 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
 [!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example"></a>例
 次の例では、列挙型、日、System.FlagsAttribute でマークされているための要件を満たしていることを示します。

 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
 [!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>関連規則
 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>関連項目
 <xref:System.FlagsAttribute?displayProperty=fullName>