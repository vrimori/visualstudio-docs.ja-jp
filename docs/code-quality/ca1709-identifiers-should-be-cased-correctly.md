---
title: 'CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0cf5b5bba2339b7b7fad84420e1ee148d6fee3b7
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548778"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません
|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|– アセンブリ、名前空間、型、メンバー、およびパラメーターで発生した場合。<br /><br /> 改行のジェネリック型パラメーターで発生した場合。|

## <a name="cause"></a>原因
 識別子の名前の小文字が正しくありません。

 \- または -

 2 文字の頭字語を含む識別子の名前と、2 番目の文字は小文字です。

 \- または -

 識別子の名前には、次の 3 つ以上の大文字の頭字語が含まれています。

## <a name="rule-description"></a>規則の説明
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 この一貫性では、学習曲線を新しいソフトウェア ライブラリに必要なライブラリがマネージ コード開発の専門知識を持つユーザーによって開発された、顧客の信頼度が高まりますが減少します。

 慣例により、パラメーター名は camel 形式の大文字小文字の区別、および名前空間、型を使用して、メンバー名は pascal 形式を使用して大文字小文字の区別します。 Camel 形式名では、最初の文字は、小文字と名の残りの単語の最初の文字が大文字です。 名の camel 形式の例は`packetSniffer`、 `ioFile`、および`fatalErrorCode`します。 Pascal 形式の名前には、最初の文字の大文字と名の残りの単語の最初の文字が大文字です。 Pascal 形式の名前の例は、 `PacketSniffer`、 `IOFile`、および`FatalErrorCode`します。

 このルールは、名は大文字と小文字の単語に分割し、2 文字の単語を"In"などの一般的な 2 文字の単語または"My"の一覧を確認します。 一致が見つからない場合、単語は頭字語と見なされます。 さらに、このルールでは、名前には、いずれかの行に 4 つの大文字または名前の最後の行に 3 つの大文字が含まれている場合、頭字語が前提としています。

 慣例により、2 文字の頭字語はすべて大文字を使用して、3 文字以上の頭字語は pascal 形式を使用して大文字小文字の区別します。 この名前付け規則を使用して、次の例: 'DB'、'CR'、'Cpa' および 'Ecma'。 次の例では、規則に違反: 'Io'、'XML' および 'DoD' と、非パラメーター名、'xp' および 'cpl'。

 'ID' は、この規則の違反が発生する特殊なケースです。 'Id' は、頭字語ではありませんが、'id' の省略形です。

## <a name="how-to-fix-violations"></a>違反の修正方法
 名前を変更するは、大文字と小文字を正しく区別できるようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 名前付けの規則がある場合、または識別子は、適切な名前、たとえば、企業やテクノロジの名を表している場合、この警告を抑制しても安全です。

 特定の用語、略語、および頭字語を追加することも、コード分析カスタム辞書にします。 ユーザー辞書に指定された語句では、この規則の違反は発生しません。 詳細については、次を参照してください[方法: コード分析辞書をカスタマイズする。](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>関連するルール
 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)