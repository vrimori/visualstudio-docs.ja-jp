---
title: 'CA1702: 複合語を正しく使い分ける |Microsoft Docs'
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
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c9a5e532391937963108d405178571d02687d1af
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535752"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 の最新ドキュメントについては、次を参照してください。 [CA1702: 複合語では、大文字と小文字が正しく区別する必要があります](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly)docs.microsoft.com でリリースされました。  
  
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|カテゴリ|Microsoft.Naming|  
|互換性に影響する変更点|互換性に影響する場合に、アセンブリに発生します。<br /><br /> 改行の型パラメーターで発生した場合。|  
  
## <a name="cause"></a>原因  
 複数の単語を含む識別子の名前と少なくとも 1 つの単語を正しく大文字と小文字されませんの複合語が表示されます。  
  
## <a name="rule-description"></a>規則の説明  
 識別子の名前は大文字小文字の区別に基づく単語に分割されます。 Microsoft のスペル チェック ライブラリでは、隣接する 2 つの単語の組み合わせがチェックされます。 認識されると、識別子は、規則違反を生成します。 違反を引き起こす複合語の例は、"CheckSum"、「マルチパート」は、"Checksum"、「マルチパート」としてそれぞれ小文字する必要があります。 ルールに組み込まれているいくつかの例外により、以前の一般的な使用方法と、1 つの単語がいくつかのフラグが設定されますが、「ツールバー」、"Filename"など (ここで、「ツールバー」および"FileName") の 2 つの個別の単語として小文字する必要があります。  
  
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージド コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 名前を変更するは、大文字と小文字を正しく区別できるようにします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 複合語の両方の部分は、スペル チェック辞書によって認識され、目的は、2 つの単語を使用する場合は、この規則による警告を抑制するのには安全です。  
  
## <a name="related-rules"></a>関連規則  
 [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>関連項目  
 [名前付けのガイドライン](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)   
 [大文字の使用規則](http://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)

