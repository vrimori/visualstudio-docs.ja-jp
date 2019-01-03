---
title: CA1701:リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2cc74bb7d3cc15e593d465a8c8d0d55275954ff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841782"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701:リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

リソース文字列には、正しく大文字と小文字に表示されていない複合語が含まれています。

## <a name="rule-description"></a>規則の説明

リソース文字列内の各単語は、大文字と小文字に基づいてトークンに分割されます。 Microsoft スペル チェック ライブラリは、隣接する 2 つのトークンの組み合わせを個別にチェックします。 それらが認識されると、その語はこの規則への違反となります。 違反を引き起こす複合語の例は、"CheckSum"、「マルチパート」は、"Checksum"、「マルチパート」としてそれぞれ小文字する必要があります。 前の一般的な使用方法によりいくつかの例外は、そのルールに組み込まれているし、「ツールバー」および"Filename"を 2 つの語として使い分けるなどのいくつかの 1 つの単語をフラグします。 この例では、「ツールバー」および"FileName"はフラグが付けられます。

名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージド コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。

## <a name="how-to-fix-violations"></a>違反の修正方法

単語を変更するは、大文字と小文字を正しく区別できるようにします。

## <a name="change-the-dictionary-language"></a>辞書の言語を変更します。

既定では、スペル チェックの英語 (en) バージョンが使用されます。 スペル チェックの言語を変更する場合は、行うことができますを追加して、次のいずれかの属性を*AssemblyInfo.cs*または*AssemblyInfo.vb*ファイル。

- 使用<xref:System.Reflection.AssemblyCultureAttribute>場合は、リソースがサテライト アセンブリには、カルチャを指定します。
- 使用<xref:System.Resources.NeutralResourcesLanguageAttribute>を指定する、*ニュートラル カルチャ*リソースが、コードと同じアセンブリ内にある場合、アセンブリの。

> [!IMPORTANT]
> 英語ベースのカルチャ以外に、カルチャを設定すると、このコード分析規則はサイレント モードで無効になっています。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

複合語の両方の部分は、スペル チェック辞書によって認識され、目的は、2 つの単語を使用する場合は、この規則による警告を抑制するのには安全です。

複合語は、スペル チェッカーのユーザー辞書に追加することもできます。 カスタム辞書で単語では、違反が発生しません。 詳細については、「[方法 :コード分析辞書をカスタマイズ](../code-quality/how-to-customize-the-code-analysis-dictionary.md)します。

## <a name="related-rules"></a>関連するルール

- [CA1702:複合語では、大文字と小文字が正しく区別する必要があります。](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA 1709:識別子では、大文字と小文字が正しく区別する必要があります。](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708:識別子は、ケース以外で相違させる必要があります。](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>関連項目

- [大文字の使用規則](/dotnet/standard/design-guidelines/capitalization-conventions)
- [名前付けのガイドライン](/dotnet/standard/design-guidelines/naming-guidelines)