---
title: 'CA1820: 文字列の長さを使用して空の文字列をテストします'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29af0d1ffacf3ec6b327228c242a0c6048e3216a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: 文字列の長さを使用して空の文字列をテストします
|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 文字列が空の文字列を使用して<xref:System.Object.Equals%2A?displayProperty=fullName>です。

## <a name="rule-description"></a>規則の説明
 使用して文字列を比較する、<xref:System.String.Length%2A?displayProperty=fullName>プロパティまたは<xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName>メソッドが使用するよりもはるかに高速<xref:System.Object.Equals%2A>です。 これは、ため<xref:System.Object.Equals%2A>よりはるかに多くの MSIL 命令を実行<xref:System.String.IsNullOrEmpty%2A>または取得するために実行する命令の数、<xref:System.String.Length%2A>プロパティ値し、0 と比較します。

 注意すべきを<xref:System.Object.Equals%2A>と<xref:System.String.Length%2A>= = 0 が null の文字列の動作が異なる。 値を取得しようとする場合、<xref:System.String.Length%2A>プロパティは、null 文字列を共通言語ランタイムをスロー、<xref:System.NullReferenceException?displayProperty=fullName>です。 共通言語ランタイムが; 例外をスローしません、null 文字列と空の文字列比較を実行する場合比較を返します`false`です。 Null をテストする 2 つの方法の相対的なパフォーマンスが大幅に影響しません。 対象とするときに[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]を使用して、<xref:System.String.IsNullOrEmpty%2A>メソッドです。 それ以外の場合を使用して、<xref:System.String.Length%2A>比較可能な限りを = = です。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、変更に使用する比較、<xref:System.String.Length%2A>プロパティと、null 文字列をテストします。 対象とする場合[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]を使用して、<xref:System.String.IsNullOrEmpty%2A>メソッドです。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 パフォーマンスに問題がない場合、この規則による警告を抑制しても安全です。

## <a name="example"></a>例
 次の例では、空の文字列を検索に使用されるさまざまな手法を示します。

 [!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]