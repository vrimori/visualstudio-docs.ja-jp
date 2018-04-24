---
title: 'CA1018: 属性を AttributeUsageAttribute に設定します'
ms.date: 11/04/2016
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
ms.workload:
- multiple
ms.openlocfilehash: 7949477e7fec9e215fd84eaa15d937be969fa102
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
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
 カスタム属性を定義するときに使用してマーク<xref:System.AttributeUsageAttribute>のソース コードで、カスタム属性を適用できる位置を示します。 属性の意味と用途によって、コード内の有効な位置が決まります。 たとえば、ユーザーの責任者を維持およびライブラリでは、各型の強化と責任は、型レベルで常に割り当てられている担当者を識別する属性を定義する可能性があります。 この場合、コンパイラはクラス、列挙型、およびインターフェイスの属性を有効にする必要がありますが、有効にしないでください、メソッド、イベント、またはプロパティ。 組織のポリシーおよび手順は、属性をアセンブリに有効にするかどうかによって決まります。

 <xref:System.AttributeTargets?displayProperty=fullName>列挙体は、カスタム属性に対して指定できるターゲットを定義します。 省略した場合<xref:System.AttributeUsageAttribute>で定義されているに、カスタム属性がすべてのターゲットに対して有効である、`All`の値<xref:System.AttributeTargets>列挙します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するを使用して、属性のターゲットを指定<xref:System.AttributeUsageAttribute>です。 次の例を参照してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 メッセージを除外するのではなく、この規則違反を修正する必要があります。 属性を継承する場合でも<xref:System.AttributeUsageAttribute>属性は、コードの保守を簡単に存在する必要があります。

## <a name="example"></a>例
 次の例では、2 つの属性を定義します。 `BadCodeMaintainerAttribute` 正しくない省略、<xref:System.AttributeUsageAttribute>ステートメント、および`GoodCodeMaintainerAttribute`ここに記載されている属性を正しく実装します。 注意してくださいプロパティ`DeveloperName`設計規則に必要な[ca 1019: 属性引数にアクセサーを定義する](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)完全を期すのために含まれています。

 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>関連規則
 [CA1019: 属性引数にアクセサーを定義します](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: シールされていない属性を使用しません](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>関連項目
 [属性](/dotnet/standard/design-guidelines/attributes)