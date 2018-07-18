---
title: 'CA2234: 文字列の代わりに System.Uri オブジェクトを渡します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07e0bbaa05b0674666a7d4403daeeee8b23348be
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919978"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: 文字列の代わりに System.Uri オブジェクトを渡します
|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 名前持つにはには、"uri"、"Uri"、"urn"、"Urn"、"url"または"Url"; が含まれています。 文字列パラメーターを持つメソッドに、呼び出しが行われますメソッドの宣言する型には持つ対応するメソッド オーバー ロードが含まれています、<xref:System.Uri?displayProperty=fullName>パラメーター。

## <a name="rule-description"></a>規則の説明
 パラメーター名は、camel 形式の大文字と小文字の規則に基づいて、トークンに分割し、各トークンが"uri"、"Uri"、"urn"、"Urn"、"url"または"Url"と等しいかどうかを表示するチェックします。 一致がある場合、パラメーターは uniform resource identifier (URI) を表すと見なされます。 URI の文字列表現は解析エラーやエンコーディング エラーが発生しやすく、セキュリティ上の脆弱性の原因となる場合があります。 <xref:System.Uri>クラスは、安全性とセキュリティで保護された方法でこれらのサービスを提供します。 ユーザーを受け取るオーバー ロードを選択する必要がありますで URI の形式に関するのみが異なる 2 つのオーバー ロード間の選択肢がある場合、<xref:System.Uri>引数。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するを受け取るオーバー ロードを呼び出して、<xref:System.Uri>引数。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 文字列パラメーターが URI を表していない場合はこの規則による警告を抑制しても安全です。

## <a name="example"></a>例
 次の例は、メソッドを`ErrorProne`、ルールと、メソッドに違反して`SaferWay`、正しく呼び出す、<xref:System.Uri>オーバー ロードします。

 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA1057: 文字列 URI オーバーロードが、System.Uri オーバーロードを呼び出します](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: URI プロパティを文字列にすることはできません](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI パラメーターを文字列にすることはできません](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI 戻り値を文字列にすることはできません](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)