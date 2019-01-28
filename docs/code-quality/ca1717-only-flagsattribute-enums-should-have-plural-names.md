---
title: CA1717:FlagsAttribute 列挙型のみが複数形の名前を含んでいなければなりません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8fa009c93f049938a198eabd1a5dcc86a45caa7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957248"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717:FlagsAttribute 列挙型のみが複数形の名前を含んでいなければなりません

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照できる列挙型の名前が複数形の語で終わるし、列挙型が設定されていない、<xref:System.FlagsAttribute?displayProperty=fullName>属性。

## <a name="rule-description"></a>規則の説明
 名前付け規則で、列挙体の複数形の名前は、列挙体の 1 つ以上の値を同時に指定できることを示します。 <xref:System.FlagsAttribute>列挙体を列挙型でビットごとの操作が可能なビット フィールドとして扱うことをコンパイラに指示します。

 列挙型の 1 つの値を同時に指定することができます、専用の場合、列挙型の名前は単数形の語になります。 たとえば、週の曜日を定義する列挙可能性がありますを想定してアプリケーションで使用するため複数の曜日を指定できます。 この列挙体である必要があります、 <xref:System.FlagsAttribute> '日' を呼び出すとします。 指定する、1 日のみを許可するような列挙型は、属性はありませんし、可能性があります 'Day' と呼ばれます。

 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、ライブラリがマネージ コード開発の専門知識を持っている人によって開発されたという信頼を顧客になり、新しいソフトウェア ライブラリを習得するために必要な時間が短縮します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 列挙体の名前に単数形の語を行うかを追加、<xref:System.FlagsAttribute>します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 名前は単数形の語で終わる場合、ルールから警告を抑制しても安全です。

## <a name="related-rules"></a>関連するルール
 [CA1714:フラグ列挙型が複数形の名前](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027:FlagsAttribute で列挙をマークします。](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217:FlagsAttribute で列挙をマークしないでください。](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>関連項目

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [列挙型デザイン](/dotnet/standard/design-guidelines/enum)