---
title: 'CA1813: シールされていない属性を使用しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b861591355a47d38beec921a13643841b40e4465
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: シールされていない属性を使用しません
|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型から継承<xref:System.Attribute?displayProperty=fullName>、抽象クラスでない場合、封印されていません (`NotInheritable` Visual Basic で)。

## <a name="rule-description"></a>規則の説明
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] クラス ライブラリには、カスタム属性を取得するメソッドが用意されています。 これらのメソッドは既定では、属性の継承階層を検索します。たとえば<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName>指定した属性の型または指定された属性の型を拡張する属性の型を検索します。 属性をシールして、継承階層を検索されなくなるため、パフォーマンスを向上させることができます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、属性の型をシールまたは、抽象型です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制しても安全です。 または場合にのみ、属性階層を定義してできない属性をシール、抽象型に、これを行う必要があります。

## <a name="example"></a>例
 次の例では、この規則に適合するカスタム属性を示します。

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>関連規則
 [CA1019: 属性引数にアクセサーを定義します](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: 属性を AttributeUsageAttribute に設定します](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>関連項目
 [属性](/dotnet/standard/design-guidelines/attributes)