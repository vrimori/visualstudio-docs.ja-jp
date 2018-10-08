---
title: '2204: ca リテラル入力正しく |Microsoft Docs'
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
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 39d841fbfa9be3e3ee5764e986a9688ca4113caf
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589784"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: リテラルは正しく入力されていなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA2204: リテラルは正しく入力されなければなりません](https://docs.microsoft.com/visualstudio/code-quality/ca2204-literals-should-be-spelled-correctly)します。

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 パラメーターまたはローカライズされた文字列とリテラル文字列が必要なプロパティにリテラル文字列が使用されるメソッドのパスには、Microsoft のスペル チェック ライブラリで認識されない語が 1 つ以上が含まれています。

## <a name="rule-description"></a>規則の説明
 このルールは、パラメーターまたは 1 つのプロパティに値として渡されたリテラル文字列を確認します。 または、true は、次の場合の詳細。

-   <xref:System.ComponentModel.LocalizableAttribute>パラメーターまたはプロパティの属性が設定を true にします。

-   パラメーターまたはプロパティ名には、"Text"、"Message"または「キャプション」が含まれています。

-   Console.Write"または"Console.WriteLine メソッドに渡される文字列パラメーターの名前は、"value"または「形式」のいずれかです。

 このルールは、複合語をトークン化の単語にリテラル文字列を解析し、各単語/トークンのスペルを確認します。 解析のアルゴリズムについては、次を参照してください。 [ca 1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)します。

 既定では、スペル チェックの英語 (en) バージョンが使用されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、単語のスペルを訂正またはカスタム辞書に単語を追加します。 ユーザー辞書を使用する方法については、次を参照してください。[方法: コード分析辞書をカスタマイズ](../code-quality/how-to-customize-the-code-analysis-dictionary.md)します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 正しくスペルの単語は、新しいソフトウェア ライブラリに必要な学習曲線を削減します。

## <a name="related-rules"></a>関連規則
 [CA1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: リソース文字列は正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)



