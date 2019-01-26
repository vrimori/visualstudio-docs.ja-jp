---
title: CA1704:識別子は正しく入力されなければなりません
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cfb91c830239a61b3f7f7e58364ae41c87152321
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935658"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704:識別子は正しく入力されなければなりません

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

識別子の名前には、Microsoft のスペル チェック ライブラリで認識されない 1 つまたは複数の単語が含まれています。 このルールは、コンス トラクターまたは get などの特別な名前のメンバーを確認し、プロパティ アクセサーを設定するはありません。

## <a name="rule-description"></a>規則の説明

このルールは、トークンに識別子を解析し、各トークンのスペルをチェックします。 解析のアルゴリズムでは、次の変換を実行します。

- 大文字は、新しいトークンを開始します。 たとえば、"My"、"Name"、"Is"、"Joe"MyNameIsJoe がトークン化です。

- 複数の大文字は、最後の大文字は、新しいトークンを開始します。 たとえば、"gui"、「エディター」GUIEditor がトークン化です。

- 先頭と末尾のアポストロフィは削除されます。 たとえば、"sender"を 'sender' がトークン化です。

- アンダー スコアは、トークンの最後を示すし、削除されます。 「こんにちは」をトークン化 Hello_world の例では、"world"です。

- 埋め込みのアンパサンドは削除されます。 たとえば、(& a) マットが"format"にトークン化します。

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

このルールの違反を修正するには、単語のスペルを訂正またはカスタム辞書に単語を追加します。

### <a name="to-add-words-to-a-custom-dictionary"></a>ユーザー辞書に単語を追加するには

カスタム辞書の XML ファイルの名前*CustomDictionary.xml*します。 プロジェクトのディレクトリは、ツールのインストール ディレクトリまたはユーザーのプロファイル ツールに関連付けられているディレクトリには、ディクショナリを配置 (*%USERPROFILE%\Application Data\\.*).Visual Studio でプロジェクトにカスタム辞書を追加する方法については、次を参照してください。[方法。コード分析辞書をカスタマイズ](../code-quality/how-to-customize-the-code-analysis-dictionary.md)します。

- 認識単語/辞書/パスの下の違反が発生する必要がありますの単語を追加します。

- 認識できないワード/辞書/パスの下に違反が発生する単語を追加します。

- 非推奨の単語/辞書/パスで不使用とフラグ必要がある単語を追加します。 関連のトピックを参照してください。 [ca 1726 適切な。適切な用語を使用して、](../code-quality/ca1726-use-preferred-terms.md)詳細についてはします。

- CasingExceptions 頭字語/辞書/パスに略語の大文字小文字の規則には、例外を追加します。

ユーザー辞書ファイルの構造の例を次に示します。

```xml
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

意図的にスペル ミスの単語と、限られた、ライブラリに適用している場合にのみは、この規則による警告を抑制します。 正しくスペルの単語は、新しいソフトウェア ライブラリに必要な学習曲線を削減します。

## <a name="related-rules"></a>関連するルール

- [CA2204:リテラルは正しく入力されなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA 1703:リソース文字列を正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA 1709:識別子では、大文字と小文字が正しく区別する必要があります。](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708:識別子は、ケース以外で相違させる必要があります。](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA 1707:識別子はアンダー スコアを含めることはできません。](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA 1726: 適切な。用語を使用します](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>関連項目

- [方法: コード分析辞書をカスタマイズします。](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
