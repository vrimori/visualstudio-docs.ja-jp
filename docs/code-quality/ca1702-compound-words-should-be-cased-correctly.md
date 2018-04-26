---
title: 'CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4703c43c81df13432f45fb4ba519a02b39a839e0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|互換性に影響する場合に、アセンブリに発生します。<br /><br /> 改行の型パラメーターで発生した場合。|

## <a name="cause"></a>原因

識別子の名前に複数の語が含まれており、大文字と小文字が正しく使い分けられていない複合語が 1 つ以上あります。

## <a name="rule-description"></a>規則の説明

識別子の名前は、大文字小文字の区別に基づいて単語に分割されます。 Microsoft スペル チェック ライブラリでは、隣接する 2 つの単語の組み合わせがチェックされます。 認識される場合、識別子には、規則の違反が生成されます。 違反を引き起こす複合語には、"CheckSum"と「マルチパート」は、使い分ける"Checksum"および「マルチパート」としてそれぞれがあります。 以前の一般的な使用法によりいくつかの例外は、ルールに構築され、1 つの単語がいくつかのフラグが立てられて"Toolbar"、"Filename"などを使い分ける (ここでは、"ToolBar"、"FileName") の 2 つの語として。

名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージ コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。

## <a name="how-to-fix-violations"></a>違反の修正方法

大文字と小文字を正しく区別できるように、名前を変更します。

## <a name="language"></a>言語

スペル チェック機能は現在英語ベースのカルチャの辞書に対してのみを確認します。 追加することで、プロジェクト ファイル内のプロジェクトのカルチャを変更することができます、 **CodeAnalysisCulture**要素。

例えば:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> 英語ベースのカルチャ以外のすべてに、カルチャを設定すると、このコード分析規則はサイレント モードで無効になっています。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

複合語の両方の部分は、辞書によって認識され、その目的は 2 つの単語を使用する場合は、この規則による警告を抑制しても安全です。

## <a name="related-rules"></a>関連規則

- [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>関連項目

- [名前付けのガイドライン](/dotnet/standard/design-guidelines/naming-guidelines)
- [大文字の使用規則](/dotnet/standard/design-guidelines/capitalization-conventions)