---
title: 'Ca 1709: 識別子を正しく使い分ける |Microsoft Docs'
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
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5a06d85367ae40b05e76f89c9b1bf0dac11e1980
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535290"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 の最新ドキュメントについては、次を参照してください。 [ca 1709: 識別子では、大文字と小文字が正しく区別する必要があります](https://docs.microsoft.com/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly)docs.microsoft.com でリリースされました。  
  
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
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージド コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
 慣例により、パラメーター名は camel 形式の規則を使用してください。名前空間、型、およびメンバー名は pascal 形式を使用して大文字小文字の区別します。 Camel 形式名では、最初の文字は、小文字と名の残りの単語の最初の文字は大文字です。 名の camel 形式の例では、"packetSniffer"、"ioFile"および"fatalErrorCode"を示します。 Pascal 形式の名前には、最初の文字の大文字と名の残りの単語の最初の文字は大文字です。 Pascal 形式の名の例では、"PacketSniffer"、"IOFile"および"FatalErrorCode"を示します。  
  
 このルールは、名は大文字と小文字の単語に分割し、2 文字の単語を"In"などの一般的な 2 文字の単語または"My"の一覧を確認します。 一致が見つからない場合、単語は頭字語と見なされます。 さらに、このルールでは、名前には、いずれかの行に 4 つの大文字または名前の最後の行に 3 つの大文字が含まれている場合、頭字語が前提としています。  
  
 慣例により、2 文字の頭字語はすべて大文字を使用して、3 文字以上の頭字語は pascal 形式を使用して大文字小文字の区別します。 この名前付け規則を使用して、次の例: 'DB'、'CR'、'Cpa' および 'Ecma'。 次の例では、規則に違反: 'Io'、'XML' および 'DoD' と、nonparameter 名、'xp' および 'cpl'。  
  
 'ID' は、この規則の違反が発生する特殊なケースです。 'Id' は、頭字語ではありませんが、'id' の省略形です。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 名前を変更するは、大文字と小文字を正しく区別できるようにします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 名前付けの規則がある場合、または識別子は、適切な名前、たとえば、企業やテクノロジの名を表している場合、この警告を抑制しても安全です。  
  
 特定の用語、略語、および頭字語を追加することも、コード分析カスタム辞書にします。 ユーザー辞書に指定された語句では、この規則の違反は発生しません。 詳細については、次を参照してください[方法: コード分析辞書をカスタマイズする。](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>関連規則  
 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

