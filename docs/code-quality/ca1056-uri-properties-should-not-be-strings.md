---
title: 'Ca 1056: URI のプロパティを文字列にする必要があることはできません |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cda8af664b6ad71ce90aa7d0bf3bbe06aefc3ab0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056: URI プロパティを文字列にすることはできません
|||  
|-|-|  
|TypeName|UriPropertiesShouldNotBeStrings|  
|CheckId|CA1056|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 型は、名前持つにはには、"uri"、"Uri"、"urn"、"Urn"、"url"または"Url"が含まれています。 文字列型のプロパティを宣言します。  
  
## <a name="rule-description"></a>規則の説明  
 このルールは、プロパティ名は pascal 形式の大文字と小文字の規則に基づいて、トークンに分割し、各トークンが"uri"、"Uri"、"urn"、"Urn"、"url"または"Url"に等しいかどうかを確認します。 一致がある場合、規則が uniform resource identifier (URI) を表すことを前提とします。 URI の文字列表現は解析エラーやエンコーディング エラーが発生しやすく、セキュリティ上の脆弱性の原因となる場合があります。 <xref:System.Uri?displayProperty=fullName>クラスは、安全性とセキュリティで保護された方法でこれらのサービスを提供します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、プロパティを変更、<xref:System.Uri>型です。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 プロパティは、URI を表していない場合はこの規則による警告を抑制しても安全です。  
  
## <a name="example"></a>例  
 次の例は、型`ErrorProne`、この規則と、型に違反する`SaferWay`規則に適合します。  
  
 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1054: URI パラメーターを文字列にすることはできません](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: URI 戻り値を文字列にすることはできません](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: 文字列の代わりに System.Uri オブジェクトを渡します](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: 文字列 URI オーバーロードが、System.Uri オーバーロードを呼び出します](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)