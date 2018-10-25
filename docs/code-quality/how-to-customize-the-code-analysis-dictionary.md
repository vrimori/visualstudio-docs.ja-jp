---
title: '方法 : コード分析辞書をカスタマイズする'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 190c94d70b87306ce119a2f37cf10b0f034fede9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869289"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>方法 : コード分析辞書をカスタマイズする
コード分析では、組み込みの辞書を使用して、スペル、文法の場合も、および .NET Framework ガイドラインの他の名前付け規則でエラー コード内の識別子を確認します。 追加、削除、または用語、略語、および組み込みの辞書に頭字語を変更するカスタム辞書の Xml ファイルを作成できます。

 たとえば、コードには、という名前のクラスが含まれている**DoorKnokker**します。 コード分析は 2 つの単語の複合として名前を識別:**ドア**と**knokker**します。 警告が発生している**knokker**スペルが正しくないです。 スペルを認識するコード分析を強制するという用語を追加することができます**knokker**を追加します。

## <a name="to-create-a-custom-dictionary"></a>カスタム辞書を作成するには
 という名前のファイルを作成する**CustomDictionary.xml**します。

 次の XML 構造を使用して、カスタムの言葉を定義します。

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
 コード分析辞書の動作を変更するには、ユーザー辞書には、次の要素の内部テキ ストとして条件を追加します。

- [ディクショナリ/単語/認識/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [ディクショナリ/単語/認識されていない/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [ディクショナリ/単語/非推奨とされます/用語 [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [辞書、単語、複合/用語 [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [辞書、単語、DiscreteExceptions/用語](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [ディクショナリ/頭字語/CasingExceptions/頭字語](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> ディクショナリ/単語/認識/Word
 用語を正しいことと、コード分析を識別する用語の一覧に含めるには、ディクショナリ、単語、認識/Word 要素の内部テキ ストとしてという用語を追加します。 辞書、単語、認識/Word 要素内の用語では区別されません。

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

 認識単語/辞書/ノード内の用語は、次のコード分析ルールに適用されます。

-   [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726: 適切な用語を使用します](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204: リテラルは正しく入力されていなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> ディクショナリ/単語/認識されていない/Word
 コード分析を正しく識別する用語の一覧から用語を除外するには、スペル、ディクショナリ、単語、"認識されません"/Word 要素の内部テキ ストとして除外する条件を追加します。 辞書、単語、"認識されません"/Word 要素内の用語では区別されません。

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

 認識できないワード/辞書/ノード内の用語は、次のコード分析ルールに適用されます。

-   [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726: 適切な用語を使用します](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204: リテラルは正しく入力されていなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> ディクショナリ/単語/非推奨とされます/用語 [@PreferredAlternate]
 用語を非推奨のコード分析を識別する用語の一覧に含めるには、ディクショナリ、単語、非推奨/用語要素の内部テキ ストとしてという用語を追加します。 非推奨の用語は、単語のスペルが正しいが、使用する必要があります。

 警告に推奨される代替語句を含めると、用語の要素の PreferredAlternate 属性で、代替を指定します。 おくことができます、属性値空代替を提案したくない場合。

- ディクショナリ/言葉で廃止された用語]、[非推奨と用語の要素は区別されません。

- PreferredAlternate 属性の値は大文字小文字を区別します。 複合の代替のパスカル ケースを使用します。

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

 非推奨の単語/辞書/ノード内の用語は、次のコード分析ルールに適用されます。

-   [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1726: 適切な用語を使用します](../code-quality/ca1726-use-preferred-terms.md)

###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> 辞書、単語、複合/用語 [@CompoundAlternate]
 組み込みの辞書は、複合語ではなく、1 つの個別の用語としていくつかの用語を識別します。 コード分析は、複合語として識別する用語の一覧に、語句を含めると、用語の正しい大文字小文字の区別を指定するには、ディクショナリ、単語、複合/用語要素の内部テキ ストとしてという用語を追加します。 用語の要素の CompoundAlternate 属性では、個々 の単語 (パスカル ケース) の最初の文字を大文字で複合語を構成する個々 の単語を指定します。 内部テキ ストで指定された期間が自動的に DiscreteExceptions/辞書/単語の一覧に追加することに注意してください。

- ディクショナリ/言葉で廃止された用語]、[非推奨と用語の要素は区別されません。

- PreferredAlternate 属性の値は大文字小文字を区別します。 複合の代替のパスカル ケースを使用します。

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

 複合語/辞書/ノード内の用語は、次のコード分析ルールに適用されます。

-   [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> 辞書、単語、DiscreteExceptions/用語
 コード分析は、1 つとして識別する用語の一覧の用語を除外するには、という用語は複合語の大文字小文字の規則でオンにすると個別の単語は、ディクショナリ、単語、DiscreteExceptions/用語要素の内部テキ ストとしてという用語を追加します。 要素のディクショナリ、単語、DiscreteExceptions/用語の用語は、小文字は区別されません。

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

 DiscreteExceptions 単語/辞書/ノード内の用語は、次のコード分析ルールに適用されます。

-   [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> ディクショナリ/頭字語/CasingExceptions/頭字語
 スペルの正しいでコード分析を識別する用語の一覧に、頭字語を含めると、複合語の頭字語という用語は、大文字と小文字をオンにした場合のルールを示すには、ディクショナリ/頭字語/CasingExceptions の内部テキ ストとして用語の追加/Acronym 要素。 頭字語辞書、略語、CasingExceptions/Acronym 要素では大文字小文字を区別します。

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

 CasingExceptions 頭字語/辞書/ノード内の用語は、次のコード分析ルールに適用されます。

-   [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> ユーザー辞書をプロジェクトに適用するには

1.  **ソリューション エクスプ ローラー**、次の手順のいずれかを使用します。

2.  ディクショナリを 1 つのプロジェクトを追加するプロジェクト名を右クリックし、**既存項目の追加**します。 ファイルを指定して、**既存項目の追加** ダイアログ ボックス。

3.  2 つ以上のプロジェクト間で共有されているディクショナリを追加するには、共有するファイルを探します、**既存項目の追加** ダイアログ ボックスで、下矢印をクリックして、**追加**ボタンをクリックし、をクリックし、**リンクとして追加**.

4.  **ソリューション エクスプ ローラー**を右クリックし、 **CustomDictionary.xml**ファイル名とクリック**プロパティ**します。

5.  **ビルド アクション**一覧で、 **CodeAnalysisDictionary**します。

6.  **出力ディレクトリにコピー**一覧で、**コピーしない**します。