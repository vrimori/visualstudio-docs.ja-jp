---
title: 'Ca 1704: 識別子は正しく入力 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 90b5085e92be22099fbf6bd8729a62223b1c93aa
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589173"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: 識別子は正しく入力されなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1704: 識別子は正しく入力されなければなりません](https://docs.microsoft.com/visualstudio/code-quality/ca1704-identifiers-should-be-spelled-correctly)します。

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

-   大文字は、新しいトークンを開始します。 たとえば、"My"、"Name"、"Is"、"Joe"MyNameIsJoe がトークン化です。

-   複数の大文字は、最後の大文字は、新しいトークンを開始します。 たとえば、"gui"、「エディター」GUIEditor がトークン化です。

-   先頭と末尾のアポストロフィは削除されます。 たとえば、"sender"を 'sender' がトークン化です。

-   アンダー スコアは、トークンの最後を示すし、削除されます。 「こんにちは」をトークン化 Hello_world の例では、"world"です。

-   埋め込みのアンパサンドは削除されます。 たとえば、(& a) マットが"format"にトークン化します。

 既定では、スペル チェックの英語 (en) バージョンが使用されます。 他の言語辞書は、現時点ではありません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、単語のスペルを訂正または CustomDictionary.xml という名前のユーザー辞書に単語を追加します。 プロジェクトのディレクトリは、ツールのインストール ディレクトリまたはユーザーのプロファイル ツールに関連付けられているディレクトリには、ディクショナリを配置 (%USERPROFILE%\Application Data\\...)。プロジェクトにカスタム辞書を追加する方法について[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]を参照してください[方法: コード分析辞書をカスタマイズします。](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

-   認識単語/辞書/パスの下の違反が発生する必要がありますの単語を追加します。

-   認識できないワード/辞書/パスの下に違反が発生する単語を追加します。

-   非推奨の単語/辞書/パスで不使用とフラグ必要がある単語を追加します。 関連のトピックを参照してください。 [ca 1726 適切な: 適切な用語を使用して、](../code-quality/ca1726-use-preferred-terms.md)詳細についてはします。

-   CasingExceptions 頭字語/辞書/パスに略語の大文字小文字の規則には、例外を追加します。

 次は、ユーザー辞書ファイルの構造の例です。

```
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

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 意図的にスペル ミスの単語と、限られた、ライブラリに適用している場合にのみは、この規則による警告を抑制します。 正しくスペルの単語は、新しいソフトウェア ライブラリに必要な学習曲線を削減します。

## <a name="related-rules"></a>関連規則
 [CA2204: リテラルは正しく入力されていなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: 識別子はアンダースコアを含むことはできません](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726: 適切な用語を使用します](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>関連項目
 [方法 : コード分析辞書をカスタマイズする](../code-quality/how-to-customize-the-code-analysis-dictionary.md)



