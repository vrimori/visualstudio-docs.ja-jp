---
title: CA1056:URI プロパティを文字列にすることはできません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a237485729a31e555dd47770e295d928ffad5393
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023107"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056:URI プロパティを文字列にすることはできません

|||
|-|-|
|TypeName|UriPropertiesShouldNotBeStrings|
|CheckId|CA1056|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型は、名前が"uri"、"Uri"、"urn"、"Urn"、"url"または"Url"を格納する文字列プロパティを宣言します。

## <a name="rule-description"></a>規則の説明
 このルールは、プロパティ名は pascal 形式の大文字と小文字の規則に基づいて、トークンに分割し、各トークンが"uri"、"Uri"、"urn"、"Urn"、"url"または"Url"に等しいかどうかを確認します。 一致がある場合、ルールでは、uniform resource identifier (URI) を表すこと前提としています。 URI の文字列表現は解析エラーやエンコーディング エラーが発生しやすく、セキュリティ上の脆弱性の原因となる場合があります。 <xref:System.Uri?displayProperty=fullName>クラスは、安全かつセキュリティで保護された方法でこれらのサービスを提供します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、プロパティを変更、<xref:System.Uri>型。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 プロパティは、URI を表していない場合、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例は、型`ErrorProne`、このルールとの種類に違反する`SaferWay`ルールを満たします。

 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>関連するルール
 [CA 1054:URI パラメーターは文字列をすることはできません。](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA 1055:URI 戻り値は文字列をすることはできません。](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234:文字列の代わりに System.Uri オブジェクトを渡します](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA 1057:文字列 URI オーバー ロードは、System.Uri オーバー ロードを呼び出す](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)