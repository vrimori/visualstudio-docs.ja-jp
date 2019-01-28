---
title: CA1703:リソース文字列は正しく入力されなければなりません
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4eea177ce2b47db0319fd9a13639e97bfbe37c0b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971612"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703:リソース文字列は正しく入力されなければなりません

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

リソース文字列に Microsoft スペル チェック ライブラリで認識されない語が 1 つ以上含まれています。

## <a name="rule-description"></a>規則の説明

このルールは、単語 (複合語をトークン)、リソース文字列を解析し、各単語/トークンのスペルを確認します。 解析のアルゴリズムについては、次を参照してください。 [ca 1704。識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)します。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するには、完全な単語をスペルが正しくまたはカスタム辞書に単語を追加するを使用します。 ユーザー辞書を使用する方法については、次を参照してください。 [ca 1704。識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)します。

## <a name="change-the-dictionary-language"></a>辞書の言語を変更します。

既定では、スペル チェックの英語 (en) バージョンが使用されます。 スペル チェックの言語を変更する場合は、行うことができますを追加して、次のいずれかの属性を*AssemblyInfo.cs*または*AssemblyInfo.vb*ファイル。

- 使用<xref:System.Reflection.AssemblyCultureAttribute>場合は、リソースがサテライト アセンブリには、カルチャを指定します。
- 使用<xref:System.Resources.NeutralResourcesLanguageAttribute>を指定する、*ニュートラル カルチャ*リソースが、コードと同じアセンブリ内にある場合、アセンブリの。

> [!IMPORTANT]
> 英語ベースのカルチャ以外に、カルチャを設定すると、このコード分析規則はサイレント モードで無効になっています。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。 正しくスペルの単語は、新しいソフトウェア ライブラリを学習するために必要な時間を短縮できます。

## <a name="related-rules"></a>関連するルール

- [CA1701:リソース文字列の複合語では、大文字と小文字が正しく区別する必要があります。](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA 1704:識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204:リテラルは正しく入力されなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)