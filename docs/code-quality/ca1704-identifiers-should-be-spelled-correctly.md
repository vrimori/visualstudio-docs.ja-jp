---
title: "CA1704: 識別子は正しく入力されなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1704: 識別子は正しく入力されなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldBeSpelledCorrectly|  
|CheckId|CA1704|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## 原因  
 識別子の名前に Microsoft スペル チェック ライブラリで認識されない語が 1 つ以上含まれています。  この規則では、コンストラクターや get および set プロパティ アクセサーなどの特殊な名前のメンバーはチェックの対象となりません。  
  
## 規則の説明  
 この規則では、識別子をトークンに分割し、個々のトークンのスペルをチェックします。  解析アルゴリズムにより、次の変換が行われます。  
  
-   大文字で始まる語が 1 つのトークンと見なされます。  たとえば、MyNameIsJoe は "My"、"Name"、"Is"、"Joe" にトークン化されます。  
  
-   複数の大文字が続く場合は、最後の大文字が次のトークンの先頭となります。  たとえば、GUIEditor は "GUI" と "Editor" にトークン化されます。  
  
-   先頭および末尾のアポストロフィは削除されます。  たとえば、'sender' は "sender" にトークン化されます。  
  
-   アンダースコアはトークンの終わりを意味し、削除されます。  たとえば、Hello\_world は "Hello" と "world" にトークン化されます。  
  
-   途中に挿入されたアンパサンドは削除されます。  たとえば、形式は&」format "に「トークン化します。  
  
 既定では、スペル チェック機能の英語 \(en\) バージョンが使用されます。  現時点では、他の言語の辞書は使用できません。  
  
## 違反の修正方法  
 この規則違反を修正するには、単語のスペルを修正するか、違反とされた単語をカスタム辞書 CustomDictionary.xml に追加します。  この辞書は、ツールのインストール ディレクトリ、プロジェクト ディレクトリ、またはユーザーのプロファイルに属するツール固有のディレクトリ \(%USERPROFILE%\\Application Data\\...\) に置きます。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のプロジェクトにカスタム辞書を追加する方法については、「[方法 : コード分析辞書をカスタマイズする](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)」を参照してください。  
  
-   違反としない語を Dictionary\/Words\/Recognized パスに追加します。  
  
-   違反とする語を Dictionary\/Words\/Unrecognized パスに追加します。  
  
-   旧式として分類する語を Dictionary\/Words\/Deprecated パスに追加します。  詳細については、関連のトピック「[CA1726: 適切な用語を使用します](../code-quality/ca1726-use-preferred-terms.md)」を参照してください。  
  
-   頭字語の規則に対する例外を Dictionary\/Acronyms\/CasingExceptions パスに追加します。  
  
 カスタム辞書ファイルの構造の例を次に示します。  
  
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
  
## 警告を抑制する状況  
 誤ったスペルの語を意図的に使用し、その語がライブラリの一部の辞書に該当する場合のみ、この規則による警告を抑制してください。  正しいスペルの単語を使用すると、新しいソフトウェア ライブラリの習得に要する時間を短縮できます。  
  
## 関連規則  
 [CA2204: リテラルは正しく入力されていなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: 識別子はアンダースコアを含むことはできません](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726: 適切な用語を使用します](../code-quality/ca1726-use-preferred-terms.md)  
  
## 参照  
 [方法 : コード分析辞書をカスタマイズする](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)