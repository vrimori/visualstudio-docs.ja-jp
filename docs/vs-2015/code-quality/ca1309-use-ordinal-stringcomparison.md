---
title: '1309: ca 使用 StringComparison |Microsoft Docs'
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
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d244c51d06993d482cb3c8f70834c033bae3f74a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200409"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: 順序を示す StringComparison を使用します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 非言語的な文字列比較操作が設定されていない、<xref:System.StringComparison>またはにパラメーターを**序数**または**OrdinalIgnoreCase**します。

## <a name="rule-description"></a>規則の説明
 多くの文字列操作、最も重要な<xref:System.String.Compare%2A?displayProperty=fullName>と<xref:System.String.Equals%2A?displayProperty=fullName>メソッドを受け入れるオーバー ロードを提供するようになりました、<xref:System.StringComparison?displayProperty=fullName>列挙値をパラメーターとして。

 いずれかを指定すると**StringComparison.Ordinal**または**StringComparison.OrdinalIgnoreCase**、非言語的な文字列比較になります。 つまり、自然言語に固有の機能には、比較の意思決定が行われたときに無視されます。 つまり、上の決定は、単純なバイト比較に基づいており、カルチャでパラメーター化は大文字小文字の区別または等しいかどうかのテーブルを無視します。 明示的にパラメーターを設定するか、その結果、によって、 **StringComparison.Ordinal**または**StringComparison.OrdinalIgnoreCase**、コード多くの場合、速度、正確性を向上およびになります信頼性の高い。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するを受け入れるオーバー ロードに文字列の比較方法を変更、<xref:System.StringComparison?displayProperty=fullName>列挙体をパラメーターとしてどちらかを指定して**序数**または**OrdinalIgnoreCase**します。 たとえば、`String.Compare(str1, str2)` を `String.Compare(str1, str2, StringComparison.Ordinal)` に変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 ライブラリまたはアプリケーションは、限定されたローカル ユーザーのまたは現在のカルチャのセマンティクスを使用する必要がある場合は、この規則による警告を抑制しても安全です。

## <a name="see-also"></a>関連項目
 [グローバリゼーションに関する警告](../code-quality/globalization-warnings.md) [ca 1307: StringComparison の指定](../code-quality/ca1307-specify-stringcomparison.md)



