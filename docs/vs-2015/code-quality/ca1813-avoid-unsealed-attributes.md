---
title: ': Ca 1813 シールされていない属性 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c422e4e261374d591acd0630f428f139b29cfcca
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591903"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: シールされていない属性を使用しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1813: シールされていない属性](https://docs.microsoft.com/visualstudio/code-quality/ca1813-avoid-unsealed-attributes)します。

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型が継承<xref:System.Attribute?displayProperty=fullName>、抽象クラスでない場合、封印されていません (`NotInheritable` Visual Basic で)。

## <a name="rule-description"></a>規則の説明
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] クラス ライブラリには、カスタム属性を取得するメソッドが用意されています。 既定では、これらのメソッドが属性の継承階層を検索します。たとえば<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName>指定した属性の型、または指定された属性型を拡張する属性の型を検索します。 属性をシールする継承階層全体が検索を排除し、パフォーマンスを向上させることができます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則の違反を修正するには、属性の型をシールします。 または、抽象型。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 このルールから警告を抑制しても安全です。 これは、属性階層を定義して、属性をシールまたはできません、抽象型場合にのみ行う必要があります。

## <a name="example"></a>例
 次の例では、この規則に適合するカスタム属性を示します。

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1019: 属性引数にアクセサーを定義します](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: 属性を AttributeUsageAttribute に設定します](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>関連項目
 [属性](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



