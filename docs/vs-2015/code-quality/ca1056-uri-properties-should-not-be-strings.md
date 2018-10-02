---
title: 'Ca 1056: URI のプロパティを文字列にする必要があることはできません |Microsoft Docs'
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
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 05a6b4e8023bd1966dc007195f405df261b8c436
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591943"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056: URI プロパティを文字列にすることはできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1056: URI プロパティは文字列できません](https://docs.microsoft.com/visualstudio/code-quality/ca1056-uri-properties-should-not-be-strings)します。

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

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 プロパティは、URI を表していない場合、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例は、型`ErrorProne`、このルールとの種類に違反する`SaferWay`ルールを満たします。

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1054: URI パラメーターを文字列にすることはできません](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI 戻り値を文字列にすることはできません](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: 文字列の代わりに System.Uri オブジェクトを渡します](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: 文字列 URI オーバーロードが、System.Uri オーバーロードを呼び出します](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)



