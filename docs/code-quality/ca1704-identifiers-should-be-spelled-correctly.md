---
title: "Ca 1704: 識別子は正しく入力されなければ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 63b10dd1d1037ee90156505f2e73105be7a9ee63
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
-   大文字の使用は、新しいトークンを開始します。 たとえば、"My"、"Name"、"Is"、"Joe"MyNameIsJoe がトークン化です。  
  
-   複数の英大文字は、最後の文字の大文字は新しいトークンを開始します。 たとえば、"gui"、「エディター」GUIEditor がトークン化です。  
  
-   先頭および末尾のアポストロフィは削除されます。 たとえば、'sender' は、「送信者」にトークン化です。  
  
-   アンダー スコアは、トークンの最後を示すされ、削除されます。 「こんにちは」に Hello_world がトークン化などの"world"です。  
  
-   埋め込みのアンパサンドは削除されます。 たとえば、(& a) マットが"format"にトークン化します。  
  
 既定では、スペル チェックの英語 (en) バージョンを使用します。 その他の言語の辞書は現在利用できません。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、単語のスペルを訂正または CustomDictionary.xml をという名前のユーザー辞書に単語を追加します。 プロジェクト ディレクトリは、ツールのインストール ディレクトリまたはユーザーのプロファイルの下にあるツールに関連付けられているディレクトリにディクショナリに配置 (%USERPROFILE%\Application データ\\...)。プロジェクトにカスタム辞書を追加する方法について[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を参照してください[する方法: コード分析辞書をカスタマイズします。](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
-   ディクショナリ/語/認識パスの下の違反が発生する必要がありますの単語を追加します。  
  
-   認識不能ディクショナリ/語/パスの下の違反の原因には単語を追加します。  
  
-   推奨されなくなったディクショナリ/語/パス 不使用としてフラグを設定する必要がある単語を追加します。 関連するルールを参照してください[CA1726: 適切な用語を使用して](../code-quality/ca1726-use-preferred-terms.md)詳細についてはします。  
  
-   ディクショナリ/頭字語/CasingExceptions パスに略語の大文字と小文字の規則には、例外を追加します。  
  
 ユーザー辞書ファイルの構造の例を次に示します。  
  
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
 単語が意図的にスペル ミスがあると、単語が限定されたライブラリのセットに適用される場合にのみこの規則による警告は抑制されます。 正しく単語のスペルは習得するまで新しいソフトウェア ライブラリに必要な時間を減らします。  
  
## <a name="related-rules"></a>関連規則  
 [CA2204: リテラルは正しく入力されていなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: 識別子はアンダースコアを含むことはできません](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726: 適切な用語を使用します](../code-quality/ca1726-use-preferred-terms.md)  
  
## <a name="see-also"></a>参照  
 [方法 : コード分析辞書をカスタマイズする](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
