---
title: CA1820:文字列の長さを使用して空の文字列をテストします
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e290fa29f27638c327565825872e0de96bbd8bb7
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2019
ms.locfileid: "55483891"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820:文字列の長さを使用して空の文字列をテストします

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

使用して文字列が空の文字列と比較<xref:System.Object.Equals%2A?displayProperty=nameWithType>します。

## <a name="rule-description"></a>規則の説明

使用して文字列を比較する、<xref:System.String.Length%2A?displayProperty=nameWithType>プロパティまたは<xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType>メソッドが使用するよりも高速<xref:System.Object.Equals%2A>します。 これは、ため<xref:System.Object.Equals%2A>いずれかのよりもはるかに多くの MSIL 命令を実行<xref:System.String.IsNullOrEmpty%2A>または取得するために実行する命令の数、<xref:System.String.Length%2A>プロパティ値し、比較して 0。

Null 文字列は、<xref:System.Object.Equals%2A>と<xref:System.String.Length%2A>= = 0 の動作が異なる。 値を取得しようとする場合、<xref:System.String.Length%2A>プロパティは、null 文字列を共通言語ランタイムがスローされます、<xref:System.NullReferenceException?displayProperty=fullName>します。 Null 文字列と空の文字列の比較を実行する場合、共通言語ランタイムは、例外はスローされませんし、返します`false`します。 Null をテストする 2 つの方法の相対的なパフォーマンスが大幅に影響しません。 .NET Framework 2.0 以降を対象とするときに使用して、<xref:System.String.IsNullOrEmpty%2A>メソッド。 それ以外の場合、使用、 <xref:System.String.Length%2A> 0 比較可能な限り = =。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を解決するには、使用する比較を変更、<xref:System.String.Length%2A>プロパティ、null 文字列をテストします。 .NET Framework 2.0 以降を対象とする場合は、使用、<xref:System.String.IsNullOrEmpty%2A>メソッド。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

パフォーマンスに問題がない場合は、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例

次の例では、空の文字列を検索に使用されるさまざまな手法を示します。

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]