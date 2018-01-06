---
title: "方法: コード分析辞書をカスタマイズする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7fa5f88a3578998fca325500a3815b909b6ce4a9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>方法 : コード分析辞書をカスタマイズする
コード分析のスペル チェック、文法的な場合も、およびその他の名前付け規則のエラー コード内の識別子を確認する組み込みの辞書を使用して、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]ガイドラインです。 追加、削除、または条項、省略形、および組み込みの辞書に頭字語を変更するカスタム辞書 Xml ファイルを作成することができます。  
  
 たとえば、コードには、という名前のクラスが含まれている**DoorKnokker**です。 コード分析は、2 つの単語の複合として名前を識別、:**ドア**と**knokker**です。 警告が発生させるし、 **knokker**スペルが正しくないです。 コード分析スペルを認識するには、という用語を追加することができます**knokker**ユーザー辞書にします。  
  
## <a name="to-create-a-custom-dictionary"></a>カスタム辞書を作成するには  
 という名前のファイルを作成する**CustomDictionary.xml**です。  
  
 次の XML 構造を使用して、カスタムの単語を定義します。  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>knokker</Word>  
         </Unrecognized>  
         <Recognized>  
            <Word></Word>  
         </Recognized>  
         <Deprecated>  
            <Term PreferredAlternate=""></Term>  
         </Deprecated>  
         <Compound>  
            <Term CompoundAlternate=""></Term>  
         </Compound>  
         <DiscreteExceptions>  
            <Term></Term>  
         </DiscreteExceptions>  
      </Words>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym></Acronym>  
         </CasingExceptions>  
      </Acronyms>  
   </Dictionary>  
```  
  
## <a name="custom-dictionary-elements"></a>ユーザー辞書要素  
 コード分析辞書の動作を変更するには、ユーザー辞書で、次の要素の内部テキ ストとして条項を追加します。  
  
-   [ディクショナリ/語/認識/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
-   [ディクショナリ/語/認識されていない/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
-   [ディクショナリ/語/推奨されなくなりました/用語 [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
-   [辞書、単語、複合/用語 [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
-   [辞書、単語、DiscreteExceptions/用語](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
-   [ディクショナリ/頭字語/CasingExceptions/頭字語](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
###  <a name="BKMK_DictionaryWordsRecognizedWord"></a>ディクショナリ/語/認識/Word  
 含めるには、語句のスペルと正しいコード分析を識別する用語の一覧には、ディクショナリ、単語、認識/Word 要素の内部テキ ストとしてという用語を追加します。 辞書、単語、認識/Word 要素内の用語は区別されません。  
  
 **例**  
  
```  
<Dictionary>  
      <Words>  
         <Recognized>  
            <Word>knokker</Word>  
            ...  
         </Recognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 ディクショナリ/語/認識ノード内の用語は、次のコード分析ルールに適用されます。  
  
-   [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: 適切な用語を使用します](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: リテラルは正しく入力されていなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a>ディクショナリ/語/認識されていない/Word  
 用語をスペルに正しいコード分析を識別する用語の一覧から除外するには、ディクショナリ、単語、認識できない/Word 要素の内部テキ ストとして除外する用語を追加します。 辞書、単語、認識できない/Word 要素内の用語は区別されません。  
  
 **例**  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>meth</Word>  
            ...  
         </Unrecognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 認識不能ディクショナリ/語/ノード内の用語は、次のコード分析ルールに適用されます。  
  
-   [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: 適切な用語を使用します](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: リテラルは正しく入力されていなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a>ディクショナリ/語/推奨されなくなりました/用語 [@PreferredAlternate]  
 コード分析は、非推奨とを識別するための用語の一覧に含めると、用語をディクショナリ、単語、推奨されなくなった/用語要素の内部テキ ストとしてという用語を追加します。 廃止された用語では、単語のスペルが正しいが、使用する必要がありますが、します。  
  
 警告に含めると、推奨される代替語句をするには、用語の要素の PreferredAlternate 属性で、代替を指定します。 できます空にする属性の値を代替を提案したくない場合。  
  
-   ディクショナリ/言葉で廃止された用語/推奨されなくなった/用語の要素は大文字小文字が区別されません。  
  
-   PreferredAlternate 属性値は、大文字小文字を区別します。 複合の代替グリフの pascal を使用します。  
  
 **例**  
  
```  
<Dictionary>  
      <Words>  
         <Deprecated>  
            <Term PreferredAlternate="LogOn">login</Term>  
            ...  
         </Deprecated>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 推奨されなくなったディクショナリ/語/ノード内の用語は、次のコード分析ルールに適用されます。  
  
-   [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1726: 適切な用語を使用します](../code-quality/ca1726-use-preferred-terms.md)  
  
###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a>辞書、単語、複合/用語 [@CompoundAlternate]  
 組み込みのディクショナリでは、複合語ではなく、1 つの個別の用語としていくつかの用語を識別します。 複合語でコード分析を識別するための用語の一覧に用語を含めると、用語の正しい大文字小文字の区別を指定するには、ディクショナリ、単語、複合/用語要素の内部テキ ストとしてという用語を追加します。 用語の要素の CompoundAlternate 属性では、複合語 (pascal) の個々 の単語の最初の文字を大文字で構成する個々 の単語を指定します。 内部テキ ストで指定された期間を自動的に 辞書/語/DiscreteExceptions リストに追加することに注意してください。  
  
-   ディクショナリ/言葉で廃止された用語/推奨されなくなった/用語の要素は大文字小文字が区別されません。  
  
-   PreferredAlternate 属性値は、大文字小文字を区別します。 複合の代替グリフの pascal を使用します。  
  
 **例**  
  
```  
<Dictionary>  
      <Words>  
         <Compound>  
            <Term CompoundAlternate="CheckBox">checkbox</Term>  
            ...  
         </Compound>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 複合語/ディクショナリ/ノード内の用語は、次のコード分析ルールに適用されます。  
  
-   [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a>辞書、単語、DiscreteExceptions/用語  
 コード分析を 1 つとして識別するための用語の一覧の用語を除外するのには、不連続 word という用語は、複合語の大文字と小文字の規則によってオンにするとは、ディクショナリ/語/DiscreteExceptions/用語の要素の内部テキ ストとしてという用語を追加します。 辞書、単語、DiscreteExceptions/用語の要素の用語は区別されません。  
  
 **例**  
  
```  
<Dictionary>  
      <Words>  
         <DiscreteExceptions>  
            <Term>checkbox</Term>  
            ...  
         </DiscreteExceptions>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 ディクショナリ/語/DiscreteExceptions ノード内の用語は、次のコード分析ルールに適用されます。  
  
-   [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a>ディクショナリ/頭字語/CasingExceptions/頭字語  
 コード分析のスペルとを識別するための用語の一覧に頭字語を含めると、複合語の大文字と小文字によってという用語がオンになっていると頭字語のルールを示すためには、ディクショナリ/頭字語/CasingExceptions の内部テキ ストとして用語の追加/Acronym 要素。 ディクショナリ/頭字語/CasingExceptions/Acronym 要素の頭字語は大文字小文字を区別します。  
  
 **例**  
  
```  
<Dictionary>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym>NESW</Acronym>   <!-- North East South West -->  
            ...  
         </CasingExceptions>  
         ...  
      </Acronyms>  
      ...  
</Dictionary>  
  
```  
  
 ディクショナリ/頭字語/CasingExceptions ノード内の用語は、次のコード分析ルールに適用されます。  
  
-   [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a>カスタム辞書をプロジェクトに適用するには  
  
1.  **ソリューション エクスプ ローラー**、次の手順のいずれかを使用します。  
  
2.  ディクショナリを単一のプロジェクトを追加、プロジェクト名を右クリックし、をクリックして**既存項目の追加**です。 ファイルを指定、**既存項目の追加** ダイアログ ボックス。  
  
3.  2 つ以上のプロジェクト間で共有されているディクショナリを追加するで共有するファイルを探します、**既存項目の追加** ダイアログ ボックスで、下矢印をクリックして、**追加**ボタンをクリックし、をクリックして**リンクとして追加**.  
  
4.  **ソリューション エクスプ ローラー**を右クリックし、 **CustomDictionary.xml**ファイル名とクリック**プロパティ**です。  
  
5.  **ビルド アクション**一覧で、 **CodeAnalysisDictionary**です。  
  
6.  **出力ディレクトリにコピー**一覧で、**コピーしない**です。