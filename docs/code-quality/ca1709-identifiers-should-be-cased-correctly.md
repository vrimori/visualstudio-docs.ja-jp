---
title: "Ca 1709: 識別子を正しく使い分ける |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f563ca87212b6f4af45f68987469b0c1370a7a18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません
|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|カテゴリ|Microsoft.Naming|  
|互換性に影響する変更点|互換性に影響する、アセンブリ、名前空間、型、メンバー、およびパラメーターで発生するとします。<br /><br /> 改行のジェネリック型パラメーターで発生した場合。|  
  
## <a name="cause"></a>原因  
 識別子の名前が正しく大文字と小文字されません。  
  
 \- または  
  
 識別子の名前には、2 文字の頭字語が含まれているし、2 番目の文字が小文字です。  
  
 \- または  
  
 識別子の名前には、次の 3 つまたは複数の英大文字の頭字語が含まれています。  
  
## <a name="rule-description"></a>規則の説明  
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージ コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
 規則では、パラメーター名は camel 形式の組み合わせを使用してください。名前空間、型、およびメンバー名は pascal 形式を使用して大文字小文字の区別します。 Camel 形式の名前では、最初の文字は小文字、し、名前に含まれる残りの単語の最初の文字が大文字ではします。 Camel 形式の名前には、"packetSniffer"、"ioFile"、"fatalErrorCode"などがあります。 Pascal 形式の名前に最初の文字は、大文字と名の残りの単語の最初の文字は大文字です。 Pascal 形式の名前には、"PacketSniffer"、"IOFile"、"FatalErrorCode"などがあります。  
  
 このルールは、名は大文字小文字の区別に基づいて単語に分割し、"In"などの一般的な 2 文字の単語または"My"の一覧に対して、2 文字の単語を確認します。 一致が見つからない場合、その単語は頭字語と見なされます。 さらに、このルールは、名前には、いずれかの行の 4 つの大文字または名の最後の行に 3 つの大文字が含まれている場合は頭字語が検出されたと仮定します。  
  
 規則では、2 文字の頭字語がすべて大文字を使用して 3 つ以上の文字の頭字語が pascal 形式を使用して大文字小文字の区別します。 次の例は、この名前付け規則を使用します。 'DB'、'CR'、'Cpa' および 'Ecma' です。 次の例では、規則に違反する: 'Io'、'XML' および 'DoD' と、nonparameter 名前、'xp' および 'cpl' です。  
  
 'ID' は、この規則の違反が発生する、特殊な例です。 'Id' は頭字語ではありませんが、'id' の省略形はします。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 大文字と小文字を正しく区別できるように、名前を変更します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 独自の名前付け規則がある場合、または識別子は、適切な名前、たとえば、会社またはテクノロジの名を表す場合、この警告を抑制しても安全です。  
  
 特定の用語や略語、頭字語を追加することも、コード分析カスタム辞書にします。 ユーザー辞書に指定された語句では、この規則の違反は発生しません。 詳細については、次を参照してください[する方法: コード分析辞書をカスタマイズする。](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>関連規則  
 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)