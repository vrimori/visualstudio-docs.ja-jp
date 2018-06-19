---
title: 'CA1717: FlagsAttribute 列挙のみが複数形の名前を含んでいなければなりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93cc4b36372d1e5ef6c81f16dc74285c336d08cc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914576"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: FlagsAttribute 列挙のみが複数形の名前を含んでいなければなりません
|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照できる列挙型の名前が複数形の語で終わるし、列挙型がでマークされていない、<xref:System.FlagsAttribute?displayProperty=fullName>属性。

## <a name="rule-description"></a>規則の説明
 名前付け規則では、列挙体の複数形の名前が、列挙型の 1 つ以上の値を同時に指定できることを示すことを示します。 <xref:System.FlagsAttribute>列挙を有効にした列挙体のビットごとの演算をビット フィールドとして扱うことをコンパイラに指示します。

 列挙型の 1 つの値を同時に指定することができます、だけの場合、列挙体の名前は単数形の語をする必要があります。 たとえば、週の曜日を定義する列挙値可能性がありますを想定しているアプリケーションで使用する複数の曜日を指定できます。 この列挙体である必要があります、<xref:System.FlagsAttribute>呼べるものは「日」とします。 指定する 1 日だけを許可するような列挙体は、属性はありませんし、可能性があります 'Day' と呼ばれます。

 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、ライブラリがマネージ コード開発の専門知識を持つユーザーによって開発されたという信頼を顧客になり、新しいソフトウェア ライブラリを習得するために必要な時間が短縮します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 単数形の語の列挙体の名前を作成または追加、<xref:System.FlagsAttribute>です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 名前が単数形の語で終わる場合、ルールから警告を抑制しても安全です。

## <a name="related-rules"></a>関連規則
 [CA1714: フラグ列挙は、複数形の名前を含んでいなければなりません](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>関連項目
 <xref:System.FlagsAttribute?displayProperty=fullName> [列挙型のデザイン](/dotnet/standard/design-guidelines/enum)