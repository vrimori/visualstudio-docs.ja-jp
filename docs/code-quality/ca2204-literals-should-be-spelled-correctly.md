---
title: 'CA2204: リテラルは正しく入力されていなければなりません'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 81989ebce0319669a03d62a504f87a0500400cd9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: リテラルは正しく入力されていなければなりません

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

リテラル文字列はローカライズ可能なパラメーターの場合、またはプロパティのローカライズ可能な引数として渡され、文字列に Microsoft スペル チェック ライブラリで認識されない語が 1 つ以上が含まれています。

## <a name="rule-description"></a>規則の説明

このルールは、パラメーターまたはいずれかのプロパティに値として渡されたリテラル文字列をチェックまたは true は、次の場合の詳細。

- <xref:System.ComponentModel.LocalizableAttribute>パラメーターまたはプロパティの属性が設定を true にします。

- パラメーターまたはプロパティ名には、"Text"、「メッセージ」または「キャプション」が含まれています。

- 渡される文字列変数の名前、<xref:System.Console.Write%2A>または<xref:System.Console.WriteLine>メソッドは"value"または「形式」のいずれか。

このルールは、複合語をトークン化の単語にリテラル文字列を解析し、各単語またはトークンのスペルをチェックします。 解析のアルゴリズムについては、次を参照してください。 [ca 1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)です。

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

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するには、単語のスペルを訂正またはカスタム辞書に単語を追加します。 ユーザー辞書を使用する方法については、次を参照してください。[する方法: コード分析辞書をカスタマイズ](../code-quality/how-to-customize-the-code-analysis-dictionary.md)です。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。 正しく単語のスペルを減らすために必要な新しいソフトウェア ライブラリを習得するまで時間。

## <a name="related-rules"></a>関連規則

- [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)