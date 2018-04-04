---
title: 'Ca 1703: リソース文字列正しく入力されなければなりません |Microsoft ドキュメント'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1227849992cf91a208563020583b19af48b13d42
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: リソース文字列は正しく入力されなければなりません

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

リソース文字列に Microsoft スペル チェック ライブラリで認識されない語が 1 つ以上含まれています。

## <a name="rule-description"></a>規則の説明

このルールは、単語 (複合語をトークン) に、リソース文字列を解析し、各単語/トークンのスペルをチェックします。 解析のアルゴリズムについては、次を参照してください。 [ca 1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)です。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するには、完全な単語をスペルが正しくまたはカスタム辞書に単語を追加するを使用します。 ユーザー辞書を使用する方法については、次を参照してください。 [ca 1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)です。

## <a name="change-the-dictionary-language"></a>辞書の言語を変更します。

既定では、スペル チェックの英語 (en) バージョンを使用します。 スペル チェックの言語を変更する場合は、行うことができますので、追加することで、次のいずれかの属性を*AssemblyInfo.cs*または*AssemblyInfo.vb*ファイル。

- 使用して<xref:System.Reflection.AssemblyCultureAttribute>リソースがサテライト アセンブリにある場合、カルチャを指定します。
- 使用して<xref:System.Resources.NeutralResourcesLanguageAttribute>を指定する、*ニュートラル カルチャ*リソースが、コードと同じアセンブリにある場合、アセンブリのです。

> [!IMPORTANT]
> 英語ベースのカルチャ以外のすべてに、カルチャを設定すると、このコード分析規則はサイレント モードで無効になっています。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。 正しく単語のスペルでは、新しいソフトウェア ライブラリを習得するまで時間が短縮します。

## <a name="related-rules"></a>関連規則

- [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: リテラルは正しく入力されていなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)