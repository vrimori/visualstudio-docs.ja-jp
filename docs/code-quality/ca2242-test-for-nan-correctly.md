---
title: "CA2242: NaN に対して正しくがテスト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b79c2d180bab62239dcace4bcf5b49195d339946
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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