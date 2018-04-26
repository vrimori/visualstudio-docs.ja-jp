---
title: 'CA2243: 属性文字列リテラルは、正しく解析する必要があります'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6aa6fe4cf38d89e76fc7151f493aac414179064
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: 属性文字列リテラルは、正しく解析する必要があります
|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 属性の文字列リテラル パラメーターは、URL、GUID、またはバージョンは正常に解析できません。

## <a name="rule-description"></a>規則の説明
 属性が派生ため<xref:System.Attribute?displayProperty=fullName>属性がコンパイル時に使用して、定数値だけをそのコンス トラクターに渡すことができます。 属性のパラメーターを Url、Guid、およびバージョンを表す必要がありますとして入力することはできません<xref:System.Uri?displayProperty=fullName>、 <xref:System.Guid?displayProperty=fullName>、および<xref:System.Version?displayProperty=fullName>これらの型は、定数として表現できないため、します。 代わりに、文字列で表す必要があります。

 パラメーターが文字列として入力されているために、コンパイル時に正しくない形式のパラメーターを渡すことが可能です。

 このルールは、名前付けのヒューリスティックを使用して、グローバルに一意の識別子 (GUID) またはバージョンの uniform resource identifier (URI) を表すパラメーターを検索し、渡された値が正しいことを確認します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 正しい形式の URL、GUID、またはバージョンにパラメーターの文字列を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 URL、GUID、またはバージョン パラメーターを表していない場合は、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例では、この規則に違反する AssemblyFileVersionAttribute のコードを示します。

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

 次のように、ルールがトリガーされます。

-   パラメーター 'version' が含まれており、System.Version を解析できません。

-   パラメーター 'guid' が含まれており、System.Guid を解析できません。

-   パラメーター 'uri'、'urn' または 'url' が含まれており、System.Uri を解析できません。

## <a name="see-also"></a>関連項目
 [CA1054: URI パラメーターを文字列にすることはできません](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)