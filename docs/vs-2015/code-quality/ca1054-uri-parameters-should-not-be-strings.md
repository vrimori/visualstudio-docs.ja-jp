---
title: 'Ca 1054: URI パラメーターを文字列にする必要があることはできません |Microsoft Docs'
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
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f8fc894ae1f0db2f63161b3f3a9fbf0e875bbd96
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589232"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: URI パラメーターを文字列にすることはできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1054: URI パラメーターは文字列を使用していない](https://docs.microsoft.com/visualstudio/code-quality/ca1054-uri-parameters-should-not-be-strings)します。

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型は、名前持つにはには、"uri"、"Uri"、"urn"、"Urn"、"url"または"Url"が含まれています。 文字列パラメーターを持つメソッドを宣言し、型に対応するオーバー ロードを宣言しません、<xref:System.Uri?displayProperty=fullName>パラメーター。

## <a name="rule-description"></a>規則の説明
 このルールは、パラメーター名は camel 規約に基づくトークンに分割し、各トークンが"uri"、"Uri"、"urn"、"Urn"、"url"または"Url"に等しいかどうかを確認します。 一致がある場合、ルールでは、パラメーターが uniform resource identifier (URI) を表すこと前提としています。 URI の文字列表現は解析エラーやエンコーディング エラーが発生しやすく、セキュリティ上の脆弱性の原因となる場合があります。 対応するオーバー ロードで、メソッドは、URI の文字列表現を受け取り場合のインスタンスを受け取る提供される場合があります、<xref:System.Uri>クラスを安全かつセキュリティで保護された方法でこれらのサービスを提供します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するには、パラメーターを変更、<xref:System.Uri>種類です。 これは、互換性に影響する変更。 受け取るメソッドのオーバー ロードを代わりに、提供、<xref:System.Uri>パラメーターです。 これは互換性に影響しない変更です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 パラメーターが URI を表していない場合、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例は、型`ErrorProne`、このルールとの種類に違反する`SaferWay`ルールを満たします。

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1056: URI プロパティを文字列にすることはできません](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055: URI 戻り値を文字列にすることはできません](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: 文字列の代わりに System.Uri オブジェクトを渡します](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: 文字列 URI オーバーロードが、System.Uri オーバーロードを呼び出します](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)



