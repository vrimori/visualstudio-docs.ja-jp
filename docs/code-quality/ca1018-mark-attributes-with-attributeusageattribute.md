---
title: 'CA1018: 属性を AttributeUsageAttribute に設定します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a54dd39746364d6908f440ac77d7a2b8bbfdbcf6
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547621"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: 属性を AttributeUsageAttribute に設定します

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 <xref:System.AttributeUsageAttribute?displayProperty=fullName>属性は、カスタム属性に存在しません。

## <a name="rule-description"></a>規則の説明
 カスタム属性を定義するときに使用してマーク<xref:System.AttributeUsageAttribute>をソース コードで、カスタム属性を適用できる場所を示します。 属性の意味と用途によって、コード内の有効な位置が決まります。 たとえば、維持およびライブラリでは、各型の強化を担当し、責任がタイプ レベルで常に割り当てられている人を識別する属性を定義する場合があります。 この場合、コンパイラでは、クラス、列挙型、およびインターフェイスの属性を有効にする必要がありますが、有効にしないでください、メソッド、イベント、またはプロパティ。 組織のポリシーと手順は、属性をアセンブリに有効にするかどうかによって決まります。

 <xref:System.AttributeTargets?displayProperty=fullName>列挙型は、カスタム属性を指定できるターゲットを定義します。 省略した場合<xref:System.AttributeUsageAttribute>、によって定義されているように、カスタム属性が、すべてのターゲットに対して有効である、`All`の値<xref:System.AttributeTargets>列挙体。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するを使用して、属性のターゲットを指定します。<xref:System.AttributeUsageAttribute>します。 次の例を参照してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 メッセージを除外ではなく、この規則の違反を修正する必要があります。 属性が継承する場合でも<xref:System.AttributeUsageAttribute>属性は、コードのメンテナンスを簡素化するためにする必要があります。

## <a name="example"></a>例
 次の例では、2 つの属性を定義します。 `BadCodeMaintainerAttribute` 正しくない省略、<xref:System.AttributeUsageAttribute>ステートメント、および`GoodCodeMaintainerAttribute`このセクションに記載されている属性を正しく実装します。 なおプロパティ`DeveloperName`デザイン規則に必要な[ca 1019: 属性引数にアクセサーを定義](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)完全を期すのために含まれています。

 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>関連するルール
 [CA1019: 属性引数にアクセサーを定義します](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: シールされていない属性を使用しません](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>関連項目

- [属性](/dotnet/standard/design-guidelines/attributes)