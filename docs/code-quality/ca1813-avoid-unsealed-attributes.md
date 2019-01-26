---
title: CA1813:アンシールド属性を使用しません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2bdb0e39051d109ffb6aa4e02c97830cf136fbe2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037682"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813:アンシールド属性を使用しません

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

パブリック型が継承<xref:System.Attribute?displayProperty=fullName>、抽象クラスでない場合、封印されていません (`NotInheritable` Visual Basic で)。

## <a name="rule-description"></a>規則の説明

.NET Framework クラス ライブラリでは、カスタム属性を取得するメソッドを提供します。 既定では、これらのメソッドで属性の継承階層が検索されます。 たとえば、<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName>指定された属性型または指定された属性型を拡張する属性の型を検索します。 属性をシールする継承階層全体が検索を排除し、パフォーマンスを向上させることができます。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則の違反を修正するには、属性の型をシールします。 または、抽象型。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

このルールから警告を抑制しても安全です。 属性階層を定義する場合にのみ、抑制し、できない属性をシールまたは、抽象型。

## <a name="example"></a>例

次の例では、この規則に適合するカスタム属性を示します。

[!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
[!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>関連するルール

- [CA 1019:属性引数にアクセサーを定義します](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)
- [CA 1018:属性を attributeusageattribute に設定します](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>関連項目

- [属性](/dotnet/standard/design-guidelines/attributes)