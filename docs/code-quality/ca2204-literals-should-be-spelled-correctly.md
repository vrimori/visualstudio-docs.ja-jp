---
title: CA2204:リテラルに正しいスペルを要求
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e23ab1c1c245a03e88b05fb15259193bb508b69a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944312"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204:リテラルに正しいスペルを要求

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

リテラル文字列がローカライズ可能なパラメーターの場合、またはローカライズ可能なプロパティの引数として渡され、文字列に Microsoft スペル チェック ライブラリで認識されない 1 つまたは複数の単語が含まれています。

## <a name="rule-description"></a>規則の説明

このルールは、パラメーターまたは 1 つのプロパティに値として渡されたリテラル文字列を確認します。 または、true は、次の場合の詳細。

- <xref:System.ComponentModel.LocalizableAttribute>パラメーターまたはプロパティの属性が設定を true にします。

- パラメーターまたはプロパティ名には、"Text"、"Message"または「キャプション」が含まれています。

- 渡される文字列変数の名前、<xref:System.Console.Write%2A>または<xref:System.Console.WriteLine>メソッドは"value"または「形式」のいずれか。

このルールは、複合語をトークン化の単語にリテラル文字列を解析し、各単語またはトークンのスペルを確認します。 解析のアルゴリズムについては、次を参照してください。 [ca 1704。識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)します。

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

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには、単語のスペルを訂正またはカスタム辞書に単語を追加します。 ユーザー辞書を使用する方法については、次を参照してください。[方法。コード分析辞書をカスタマイズ](../code-quality/how-to-customize-the-code-analysis-dictionary.md)します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。 正しくスペルの単語は、新しいソフトウェア ライブラリに必要な学習曲線を削減します。

## <a name="related-rules"></a>関連するルール

- [CA 1704:識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA 1703:リソース文字列を正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)