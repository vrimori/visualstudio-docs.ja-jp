---
title: 'CA1304: CultureInfo を指定します'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe02dd66b523e6ee82c5e1a2051f3a68839957d4
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546194"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: CultureInfo を指定します

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

メソッドまたはコンス トラクターの呼び出しを受け入れるオーバー ロードを持つメンバーを<xref:System.Globalization.CultureInfo?displayProperty=nameWithType>パラメーター、およびメソッドまたはコンス トラクターは使用するオーバー ロードを呼び出しません、<xref:System.Globalization.CultureInfo>パラメーター。 このルールは、次のメソッドの呼び出しを無視します。

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>規則の説明

ときに、<xref:System.Globalization.CultureInfo>または<xref:System.IFormatProvider?displayProperty=nameWithType>オブジェクトが指定されていない、オーバー ロードされたメンバーによって提供される既定値はすべてのロケールに効果がありません。 また、.NET Framework のメンバーが既定のカルチャを選択し、コードの適切なことができない可能性がある前提条件に基づく書式設定します。 コードのシナリオでは、予想どおりに機能させるには、次のガイドラインに従って、カルチャに固有の情報を指定する必要があります。

- 場合は、値は、ユーザーに表示されますが、現在のカルチャを使用します。 以下を参照してください。<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>

- 場合は、値が格納され、ソフトウェアからアクセスされる、インバリアント カルチャを使用、ファイルまたはデータベースに永続化は、します。 以下を参照してください。<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>

- 値の変換先がわからない場合は、データ コンシューマーがあるか、プロバイダーが、カルチャを指定します。

オーバー ロードされたメンバーの既定の動作がニーズに適した場合でもを明示的にされるため、コードを自己文書化して保守が簡単なカルチャ固有のオーバー ロードを呼び出すことをお勧めします。

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> インスタンスを使用して、ローカライズされたリソースを取得するためだけに使用、<xref:System.Resources.ResourceManager?displayProperty=nameWithType>クラス。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するを受け取るオーバー ロードを使用して、<xref:System.Globalization.CultureInfo>引数。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

コードの保守性が重要な開発の優先順位ではないと、既定のカルチャが、適切な選択が確実である場合にこの規則による警告を抑制しても安全になります。

## <a name="example-showing-how-to-fix-violations"></a>違反を修正する方法を示す例

次の例では、`BadMethod`によりこの規則の違反が 2 つ発生します。 `GoodMethod` インバリアント カルチャを渡すことによって、最初の違反を修正<xref:System.String.Compare%2A?displayProperty=nameWithType>には、現在のカルチャを渡すことによって、2 つ目の違反を修正し、<xref:System.String.ToLower%2A?displayProperty=nameWithType>ため`string3`がユーザーに表示されます。

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>書式付き出力の例を示す

次の例では、既定値に対する現在のカルチャの効果を示します<xref:System.IFormatProvider>によって選択されている、<xref:System.DateTime>型。

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

この例を実行すると、次の出力が生成されます。

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>関連するルール

- [CA1305: IFormatProvider を指定します](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>関連項目

- [CultureInfo クラスを使用します。](/dotnet/standard/globalization-localization/globalization#Cultures)