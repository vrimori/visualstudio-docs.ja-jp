---
title: 'CA1820: 文字列の長さを使用して空の文字列をテストします'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 24850c61216354f7d9fa197dc7c4317105ab98ba
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551418"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: 文字列の長さを使用して空の文字列をテストします
|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 使用して文字列が空の文字列と比較<xref:System.Object.Equals%2A?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 使用して文字列を比較する、<xref:System.String.Length%2A?displayProperty=fullName>プロパティまたは<xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName>メソッドが使用するよりもはるかに高速<xref:System.Object.Equals%2A>します。 これは、ため<xref:System.Object.Equals%2A>いずれかのよりもはるかに多くの MSIL 命令を実行<xref:System.String.IsNullOrEmpty%2A>または取得するために実行する命令の数、<xref:System.String.Length%2A>プロパティ値し、比較して 0。

 注意すべきを<xref:System.Object.Equals%2A>と<xref:System.String.Length%2A>= = 0 が null の文字列の動作が異なる。 値を取得しようとする場合、<xref:System.String.Length%2A>プロパティは、null 文字列を共通言語ランタイムがスローされます、<xref:System.NullReferenceException?displayProperty=fullName>します。 共通言語ランタイムが; 例外をスローしません null 文字列と空の文字列の比較を実行する場合比較を返します`false`します。 Null をテストする 2 つの方法の相対的なパフォーマンスが大幅に影響しません。 対象とするときに[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]を使用して、<xref:System.String.IsNullOrEmpty%2A>メソッド。 それ以外の場合、使用、<xref:System.String.Length%2A>比較可能な限り = =。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するには、使用する比較を変更、<xref:System.String.Length%2A>プロパティ、null 文字列をテストします。 対象とする場合[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]を使用して、<xref:System.String.IsNullOrEmpty%2A>メソッド。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 パフォーマンスに問題がない場合は、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例では、空の文字列を検索に使用されるさまざまな手法を示します。

 [!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]