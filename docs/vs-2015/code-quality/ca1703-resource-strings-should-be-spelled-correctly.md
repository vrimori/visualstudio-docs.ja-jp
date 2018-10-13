---
title: 'Ca 1703: リソース文字列は正しく入力 |Microsoft Docs'
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
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 358048064624113bf15fdab7d0fe936aabc3fe94
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259469"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: リソース文字列は正しく入力されなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 リソース文字列に Microsoft スペル チェック ライブラリで認識されない語が 1 つ以上含まれています。

## <a name="rule-description"></a>規則の説明
 このルールは、単語 (複合語をトークン)、リソース文字列を解析し、各単語/トークンのスペルを確認します。 解析のアルゴリズムについては、次を参照してください。 [ca 1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)します。

 既定では、スペル チェックの英語 (en) バージョンが使用されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、完全な単語をスペルが正しくまたはカスタム辞書に単語を追加するを使用します。 ユーザー辞書を使用する方法については、次を参照してください。 [ca 1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 正しくスペルの単語は、新しいソフトウェア ライブラリを学習するために必要な時間を短縮できます。

## <a name="related-rules"></a>関連規則
 [CA1701: リソース文字列の複合語は、大文字と小文字を正しく区別しなければなりません](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: リテラルは正しく入力されていなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)



