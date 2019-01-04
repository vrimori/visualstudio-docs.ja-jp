---
title: CA2242:NaN に対して正しくテストします
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c809e6fe21bae15fed8c79c03a9210d518c157a3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838637"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242:NaN に対して正しくテストします

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 式に対して値をテストする<xref:System.Single.NaN?displayProperty=fullName>または<xref:System.Double.NaN?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 <xref:System.Double.NaN?displayProperty=fullName>、not 非数を表す場合、算術演算が定義されていない場合に発生します。 値の間で等しいかどうかをテストする任意の式と<xref:System.Double.NaN?displayProperty=fullName>は常に返します`false`します。 値の間の不等性をテストする任意の式と<xref:System.Double.NaN?displayProperty=fullName>は常に返します`true`します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正し、値を表すかどうかを正確に判断する<xref:System.Double.NaN?displayProperty=fullName>を使用して、<xref:System.Single.IsNaN%2A?displayProperty=fullName>または<xref:System.Double.IsNaN%2A?displayProperty=fullName>値をテストします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、対応する値を正しくテストする 2 つの式<xref:System.Double.NaN?displayProperty=fullName>と正しく使用する式<xref:System.Double.IsNaN%2A?displayProperty=fullName>値をテストします。

 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]