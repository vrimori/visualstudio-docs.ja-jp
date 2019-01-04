---
title: CA1055:URI 戻り値を文字列にすることはできません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d70b35b316d4299af5927759fd48601efc47b2a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838938"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055:URI 戻り値を文字列にすることはできません

|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 "Uri"、"Uri"、"urn"、"Urn"、"url"または"Url"を含むメソッドの名前と、メソッドは、文字列を返します。

## <a name="rule-description"></a>規則の説明
 このルールは、メソッド名は pascal 形式の大文字と小文字の規則に基づいて、トークンに分割し、各トークンが"uri"、"Uri"、"urn"、"Urn"、"url"または"Url"に等しいかどうかを確認します。 一致がある場合、ルールは、メソッドは、uniform resource identifier (URI) を返しますと仮定します。 URI の文字列表現は解析エラーやエンコーディング エラーが発生しやすく、セキュリティ上の脆弱性の原因となる場合があります。 <xref:System.Uri?displayProperty=fullName>クラスは、安全かつセキュリティで保護された方法でこれらのサービスを提供します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するには、戻り値の型を変更、<xref:System.Uri>します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 戻り値は、URI を表していない場合は、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例は、型`ErrorProne`、このルールとの種類に違反する`SaferWay`ルールを満たします。

 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>関連するルール
 [CA 1056:URI のプロパティには、文字列がすることはできません。](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA 1054:URI パラメーターは文字列をすることはできません。](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA 2234:文字列の代わりに System.Uri オブジェクトを渡します](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA 1057:文字列 URI オーバー ロードは、System.Uri オーバー ロードを呼び出す](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)