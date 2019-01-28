---
title: CA1306:データ型のロケールを設定します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa74ce81e7923115cf4fa07aba26be171e187690
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946556"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306:データ型のロケールを設定します

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 作成された 1 つまたは複数のメソッドまたはコンス トラクター<xref:System.Data.DataTable?displayProperty=fullName>または<xref:System.Data.DataSet?displayProperty=fullName>インスタンスし、ロケールのプロパティを明示的に設定しなかった (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName>または<xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>)。

## <a name="rule-description"></a>規則の説明
 ロケールは、数値、通貨記号、および並べ替え順序の使用を書式設定などのデータのカルチャに固有のプレゼンテーション要素を決定します。 作成するときに、<xref:System.Data.DataTable>または<xref:System.Data.DataSet>ロケールを明示的に設定する必要があります。 既定では、これらの型のロケールは、現在のカルチャです。 データベースまたはファイルに格納されているが、グローバルに共有するデータ、ロケールがインバリアント カルチャに設定する通常 (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>)。 データがカルチャ間で共有される場合、既定のロケールを使用する可能性がありますの内容、<xref:System.Data.DataTable>または<xref:System.Data.DataSet>に表示されるか、正しく解釈されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、ロケールを明示的に設定、<xref:System.Data.DataTable>または<xref:System.Data.DataSet>します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 限られたローカル ユーザーを対象にライブラリまたはアプリケーションでは、データが共有されていない、または既定の設定がサポートされているすべてのシナリオでは、目的の動作が得られますときに、この規則による警告を非表示にも安全です。

## <a name="example"></a>例
 次の例では、2 つ作成されます<xref:System.Data.DataTable>インスタンス。

 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>関連項目

- <xref:System.Data.DataTable?displayProperty=fullName>
- <xref:System.Data.DataSet?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>