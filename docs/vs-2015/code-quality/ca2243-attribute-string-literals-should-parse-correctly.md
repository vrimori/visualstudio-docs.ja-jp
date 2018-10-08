---
title: 'Ca 2243: 属性文字列リテラルは、正しく解析する必要があります |Microsoft Docs'
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
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6e1e90ccfefad3b73a950849643009a92f074d4f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47549266"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: 属性文字列リテラルは、正しく解析する必要があります
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 2243: 属性文字列リテラルは、正しく解析する必要があります](https://docs.microsoft.com/visualstudio/code-quality/ca2243-attribute-string-literals-should-parse-correctly)します。

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

 このルールは、uniform resource identifier (URI)、グローバル一意識別子 (GUID) またはバージョンを表すパラメーターを検索する名前付けのヒューリスティックを使用し、渡された値が正しいことを確認します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 パラメーター文字列を変更すると、正しい形式の URL、GUID、またはバージョン。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 パラメーターは、URL、GUID、またはバージョンを表していない場合、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 この規則に違反する assemblyfileversionattribute ものコードを次の例に示します。

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 ルールは、次のようにトリガーされます。

-   パラメーター 'version' が含まれてし、System.Version を解析できません。

-   パラメーター 'guid' が含まれており、System.Guid を解析できません。

-   パラメーター 'uri'、'urn' または 'url' が含まれており、System.Uri に解析できません。

## <a name="see-also"></a>関連項目
 [CA1054: URI パラメーターを文字列にすることはできません](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)



