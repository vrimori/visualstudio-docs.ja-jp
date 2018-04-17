---
title: 'CA2242: NaN に対して正しくがテスト |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a782c0b3f32c9733b47ded29852e006f8ba7c1aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: NaN に対して正しくテストします
|||  
|-|-|  
|TypeName|TestForNaNCorrectly|  
|CheckId|CA2242|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 式に対して値をテストする<xref:System.Single.NaN?displayProperty=fullName>または<xref:System.Double.NaN?displayProperty=fullName>です。  
  
## <a name="rule-description"></a>規則の説明  
 <xref:System.Double.NaN?displayProperty=fullName>、not 非数を表す場合、算術演算が定義されていない場合に発生します。 値間の等価性をテストする任意の式と<xref:System.Double.NaN?displayProperty=fullName>は常に返します`false`です。 値間の不等性をテストする任意の式と<xref:System.Double.NaN?displayProperty=fullName>は常に返します`true`です。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するかどうかを表す値を正確に判断して<xref:System.Double.NaN?displayProperty=fullName>を使用して<xref:System.Single.IsNaN%2A?displayProperty=fullName>または<xref:System.Double.IsNaN%2A?displayProperty=fullName>値をテストします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、2 つの式に対して値を正しくテストする<xref:System.Double.NaN?displayProperty=fullName>と正しく使用する式<xref:System.Double.IsNaN%2A?displayProperty=fullName>値をテストします。  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]