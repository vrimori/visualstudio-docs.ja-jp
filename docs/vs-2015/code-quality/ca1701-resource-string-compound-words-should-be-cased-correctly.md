---
title: 'CA1701: リソース文字列の複合語を正しく使い分ける |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a7212b5b629ef6cd15901c76c755d01c0efe17e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921933"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 リソース文字列には、正しく大文字と小文字に表示されていない複合語が含まれています。

## <a name="rule-description"></a>規則の説明
 リソース文字列内の各単語は、大文字と小文字に基づいてトークンに分割されます。 Microsoft スペル チェック ライブラリは、隣接する 2 つのトークンの組み合わせを個別にチェックします。 それらが認識されると、その語はこの規則への違反となります。 違反を引き起こす複合語の例は、"CheckSum"、「マルチパート」は、"Checksum"、「マルチパート」としてそれぞれ小文字する必要があります。 前の一般的な使用方法によりいくつかの例外は、そのルールに組み込まれているし、「ツールバー」および"Filename"を 2 つの語として使い分けるなどのいくつかの 1 つの単語をフラグします。 この例では、「ツールバー」および"FileName"はフラグが付けられます。

 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージド コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 単語を変更するは、大文字と小文字を正しく区別できるようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 複合語の両方の部分は、スペル チェック辞書によって認識され、目的は、2 つの単語を使用する場合は、この規則による警告を抑制するのには安全です。

 複合語は、スペル チェッカーのユーザー辞書に追加することもできます。 カスタム辞書で単語では、違反が発生しません。 詳細については、次を参照してください。[方法: コード分析辞書をカスタマイズ](../code-quality/how-to-customize-the-code-analysis-dictionary.md)します。

## <a name="related-rules"></a>関連規則
 [CA1702: 複合語では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>関連項目
 [大文字と小文字の表記規則](http://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)[名前付けのガイドライン](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)



