---
title: 'CA1309: 順序を示す StringComparison を使用します'
ms.date: 11/04/2016
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
ms.openlocfilehash: 964dfee8b8ed78de76ead4ee5eda63fe0a49a72c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: 順序を示す StringComparison を使用します
|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 非言語的な文字列比較操作が設定されていない、<xref:System.StringComparison>またはにパラメーターを**序数**または**OrdinalIgnoreCase**です。

## <a name="rule-description"></a>規則の説明
 多くの文字列操作、最も重要な<xref:System.String.Compare%2A?displayProperty=fullName>と<xref:System.String.Equals%2A?displayProperty=fullName>、メソッドを受け入れるオーバー ロードを提供するようになりました、<xref:System.StringComparison?displayProperty=fullName>をパラメーターとしての列挙値。

 いずれかを指定すると**StringComparison.Ordinal**または**StringComparison.OrdinalIgnoreCase**、非言語的な文字列の比較になります。 つまり、比較が決定されます、自然言語に固有の機能は無視されます。 つまり、上の決定は、単純なバイト比較に基づいており、大文字と小文字または同等の表のカルチャでパラメーター化されるを無視します。 いずれかにパラメーターを明示的に設定してその結果、 **StringComparison.Ordinal**または**StringComparison.OrdinalIgnoreCase**、コード多くの場合、速度の向上が正しいかどうか、なりが信頼性の高い。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、文字列比較のメソッドを変更を受け入れるオーバー ロードに、<xref:System.StringComparison?displayProperty=fullName>列挙体をパラメーターとしてどちらかを指定して**序数**または**OrdinalIgnoreCase**です。 たとえば、`String.Compare(str1, str2)` を `String.Compare(str1, str2, StringComparison.Ordinal)` に変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 ライブラリまたはアプリケーションは、限定されたローカル ユーザーのまたは現在のカルチャのセマンティクスを使用する必要がある場合は、この規則による警告を抑制しても安全です。

## <a name="see-also"></a>関連項目
 [グローバリゼーションに関する警告](../code-quality/globalization-warnings.md) [ca 1307: StringComparison の指定](../code-quality/ca1307-specify-stringcomparison.md)