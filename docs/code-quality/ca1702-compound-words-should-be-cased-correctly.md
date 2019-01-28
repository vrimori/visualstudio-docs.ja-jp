---
title: CA1702:複合語では、大文字と小文字が正しく区別されなければなりません
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67d697ac5c441efaf78fa7382b9efdead647eec8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996507"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702:複合語では、大文字と小文字が正しく区別されなければなりません

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|互換性に影響する場合に、アセンブリに発生します。<br /><br /> 改行の型パラメーターで発生した場合。|

## <a name="cause"></a>原因

識別子の名前に複数の語が含まれており、大文字と小文字が正しく使い分けられていない複合語が 1 つ以上あります。

## <a name="rule-description"></a>規則の説明

識別子の名前は大文字小文字の区別に基づく単語に分割されます。 Microsoft のスペル チェック ライブラリでは、隣接する 2 つの単語の組み合わせがチェックされます。 認識されると、識別子は、規則違反を生成します。 違反を引き起こす複合語の例は、"CheckSum"、「マルチパート」は、"Checksum"、「マルチパート」としてそれぞれ小文字する必要があります。 ルールに組み込まれているいくつかの例外により、以前の一般的な使用方法と、1 つの単語がいくつかのフラグが設定されますが、「ツールバー」、"Filename"など (ここで、「ツールバー」および"FileName") の 2 つの個別の単語として小文字する必要があります。

名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージド コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。

## <a name="how-to-fix-violations"></a>違反の修正方法

名前を変更するは、大文字と小文字を正しく区別できるようにします。

## <a name="language"></a>言語

スペル チェックは現在英語ベースのカルチャのディクショナリのみに対して確認します。 追加することで、プロジェクト ファイルで、プロジェクトのカルチャを変更することができます、 **CodeAnalysisCulture**要素。

例:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> 英語ベースのカルチャ以外に、カルチャを設定すると、このコード分析規則はサイレント モードで無効になっています。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

複合語の両方の部分は、スペル チェック辞書によって認識され、目的は、2 つの単語を使用する場合は、この規則による警告を抑制するのには安全です。

## <a name="related-rules"></a>関連するルール

- [CA1701:リソース文字列の複合語では、大文字と小文字が正しく区別する必要があります。](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA 1709:識別子では、大文字と小文字が正しく区別する必要があります。](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708:識別子は、ケース以外で相違させる必要があります。](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>関連項目

- [名前付けのガイドライン](/dotnet/standard/design-guidelines/naming-guidelines)
- [大文字の使用規則](/dotnet/standard/design-guidelines/capitalization-conventions)