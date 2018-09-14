---
title: 'CA1309: 順序を示す StringComparison を使用します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91953fd855576b6f40d02ebb3653fff07bfdef9c
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546432"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: 順序を示す StringComparison を使用します

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

非言語的な文字列比較操作が設定されていない、<xref:System.StringComparison>またはにパラメーターを**序数**または**OrdinalIgnoreCase**します。

## <a name="rule-description"></a>規則の説明
 多くの文字列操作、最も重要なは、<xref:System.String.Compare%2A?displayProperty=fullName>と<xref:System.String.Equals%2A?displayProperty=fullName>メソッドを受け入れるオーバー ロードを提供するようになりました、<xref:System.StringComparison?displayProperty=fullName>列挙値をパラメーターとして。

 いずれかを指定すると**StringComparison.Ordinal**または**StringComparison.OrdinalIgnoreCase**、文字列比較では、非言語的な。 つまり、自然言語に固有の機能には、比較の意思決定が行われたときに無視されます。 自然言語の機能を無視して、上の決定はベースの単純なバイト比較と大文字小文字の区別やカルチャでパラメーター化される同等の表ではなくを意味します。 明示的にパラメーターを設定するか、その結果、によって、 **StringComparison.Ordinal**または**StringComparison.OrdinalIgnoreCase**、コード多くの場合、速度、正確性を向上およびになります信頼性の高い。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するを受け入れるオーバー ロードに文字列の比較方法を変更、<xref:System.StringComparison?displayProperty=fullName>列挙体をパラメーターとしてどちらかを指定して**序数**または**OrdinalIgnoreCase**します。 たとえば、`String.Compare(str1, str2)` を `String.Compare(str1, str2, StringComparison.Ordinal)` に変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 ライブラリまたはアプリケーションが制限されたローカルの対象ユーザーのためのものである場合、または、現在のカルチャのセマンティクスを使用する必要があります、この規則による警告を抑制しても安全になります。

## <a name="see-also"></a>関連項目

- [グローバリゼーションに関する警告](../code-quality/globalization-warnings.md)
- [CA1307: StringComparison の指定](../code-quality/ca1307-specify-stringcomparison.md)