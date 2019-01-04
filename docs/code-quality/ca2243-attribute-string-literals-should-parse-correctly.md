---
title: CA2243:属性文字列リテラルは、正しく解析する必要があります
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: b6c7aa4638a1a0a863bf53c85a5e182f57a366d8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939993"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243:属性文字列リテラルは、正しく解析する必要があります

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 属性の文字列リテラル パラメーターは URL、GUID、またはバージョンとして正しく解析できません。

## <a name="rule-description"></a>規則の説明
 派生した属性があるため<xref:System.Attribute?displayProperty=fullName>、および属性がコンパイル時に使用される、定数値のみをそのコンス トラクターに渡すことができます。 Url、Guid、およびバージョンを表す必要があります属性のパラメーターとして入力することはできません<xref:System.Uri?displayProperty=fullName>、 <xref:System.Guid?displayProperty=fullName>、および<xref:System.Version?displayProperty=fullName>定数としてこれらの型を表すことができないためです。 代わりに、文字列で表す必要があります。

 パラメーターは、文字列として型指定された、ために、コンパイル時に正しくない形式のパラメーターを渡すことができることができます。

 このルールは、uniform resource identifier (URI)、グローバルに一意の識別子 (GUID)、またはバージョンを表すパラメーターを検索する名前付けのヒューリスティックを使用し、渡された値が正しいことを確認します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 パラメーター文字列を変更すると、正しい形式の URL、GUID、またはバージョン。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 パラメーターは、URL、GUID、またはバージョンを表していない場合、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 この規則に違反する assemblyfileversionattribute ものコードを次の例に示します。

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

 ルールは、次のパラメーターによってトリガーされます。

- パラメーター 'version' が含まれてし、System.Version を解析できません。

- パラメーター 'guid' が含まれており、System.Guid を解析できません。

- パラメーター 'uri'、'urn' または 'url' が含まれており、System.Uri に解析できません。

## <a name="see-also"></a>関連項目

- [CA 1054:URI パラメーターは文字列をすることはできません。](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)