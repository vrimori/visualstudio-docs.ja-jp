---
title: 'CA1704: 識別子は正しく入力されなければなりません'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6fe8c51ce1fc2bd93fca26b52b3ef5daf223b8b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: 識別子は正しく入力されなければなりません

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

識別子の名前には、Microsoft スペル チェック ライブラリで認識されない語が 1 つ以上が含まれています。 このルールのコンス トラクターまたは get などの特別な名前のメンバーを確認および set プロパティ アクセサーはありません。

## <a name="rule-description"></a>規則の説明

このルールは、トークンに識別子を解析し、各トークンのスペルをチェックします。 解析のアルゴリズムでは、次の変換を実行します。

- 大文字の使用は、新しいトークンを開始します。 たとえば、"My"、"Name"、"Is"、"Joe"MyNameIsJoe がトークン化です。

- 複数の英大文字は、最後の文字の大文字は新しいトークンを開始します。 たとえば、"gui"、「エディター」GUIEditor がトークン化です。

- 先頭および末尾のアポストロフィは削除されます。 たとえば、'sender' は、「送信者」にトークン化です。

- アンダー スコアは、トークンの最後を示すされ、削除されます。 「こんにちは」に Hello_world がトークン化などの"world"です。

- 埋め込みのアンパサンドは削除されます。 たとえば、(& a) マットが"format"にトークン化します。

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

この規則違反を修正するには、単語のスペルを訂正またはカスタム辞書に単語を追加します。

### <a name="to-add-words-to-a-custom-dictionary"></a>ユーザー辞書に単語を追加するには

ユーザー辞書の XML ファイルの名前を付けます*CustomDictionary.xml*です。 プロジェクト ディレクトリは、ツールのインストール ディレクトリまたはユーザーのプロファイルの下にあるツールに関連付けられているディレクトリにディクショナリに配置 (*%USERPROFILE%\Application データ\\.*).Visual Studio でプロジェクトにカスタム辞書を追加する方法については、次を参照してください。[する方法: コード分析辞書をカスタマイズ](../code-quality/how-to-customize-the-code-analysis-dictionary.md)です。

- ディクショナリ/語/認識パスの下の違反が発生する必要がありますの単語を追加します。

- 認識不能ディクショナリ/語/パスの下の違反の原因には単語を追加します。

- 推奨されなくなったディクショナリ/語/パス 不使用としてフラグを設定する必要がある単語を追加します。 関連するルールを参照してください[CA1726: 適切な用語を使用して](../code-quality/ca1726-use-preferred-terms.md)詳細についてはします。

- ディクショナリ/頭字語/CasingExceptions パスに略語の大文字と小文字の規則には、例外を追加します。

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

単語が意図的にスペル ミスがあると、単語が限定されたライブラリのセットに適用される場合にのみこの規則による警告は抑制されます。 正しく単語のスペルは習得するまで新しいソフトウェア ライブラリに必要な時間を減らします。

## <a name="related-rules"></a>関連規則

- [CA2204: リテラルは正しく入力されていなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: 識別子はアンダースコアを含むことはできません](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: 適切な用語を使用します](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>関連項目

- [方法 : コード分析辞書をカスタマイズする](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
