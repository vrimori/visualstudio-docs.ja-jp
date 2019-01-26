---
title: CA1305:IFormatProvider を指定します
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 55ecfa146958819092c51055e039f57e8c1b3f6e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018710"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305:IFormatProvider を指定します

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

メソッドまたはコンス トラクターの呼び出しを受け入れるオーバー ロードを持つ 1 つまたは複数のメンバー、<xref:System.IFormatProvider?displayProperty=fullName>パラメーター、およびメソッドまたはコンス トラクターは使用するオーバー ロードを呼び出しません、<xref:System.IFormatProvider>パラメーター。

このルールを無視してとして説明されている .NET Framework のメソッドの呼び出しは無視されます、<xref:System.IFormatProvider>パラメーター。 ルールには、次のメソッドも無視されます。

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>規則の説明

ときに、<xref:System.Globalization.CultureInfo?displayProperty=nameWithType>または<xref:System.IFormatProvider>オブジェクトが指定されていない、オーバー ロードされたメンバーによって提供される既定値はすべてのロケールに効果がありません。 また、.NET Framework のメンバーが既定のカルチャを選択し、コードの適切なことができない可能性がある前提条件に基づく書式設定します。 コードが、シナリオのために期待どおりに動作することを確認するには、次のガイドラインに従って、カルチャに固有の情報を指定する必要があります。

- 場合は、値は、ユーザーに表示されますが、現在のカルチャを使用します。 以下を参照してください。<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>

- 値が格納され、ソフトウェア (ファイルまたはデータベースに保存される) からアクセスされる場合、は、インバリアント カルチャを使用します。 以下を参照してください。<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>

- 値の変換先がわからない場合は、データ コンシューマーがあるか、プロバイダーが、カルチャを指定します。

オーバー ロードされたメンバーの既定の動作がニーズに適した場合でもを明示的にされるため、コードを自己文書化して保守が簡単なカルチャ固有のオーバー ロードを呼び出すことをお勧めします。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するを受け取るオーバー ロードを使用して、<xref:System.IFormatProvider>引数。 または、使用して、 [C# 文字列補間する](/dotnet/csharp/tutorials/string-interpolation)に渡すと、<xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType>メソッド。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

コードの保守性が重要な開発の優先順位ではないと、既定の形式が適切な選択が確実である場合にこの規則による警告を抑制しても安全です。

## <a name="example"></a>例

次のコードで、`example1`文字列 CA1305 ルールに違反しています。 `example2`文字列を渡すことによって CA1305 ルールを満たす<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>、実装する<xref:System.IFormatProvider>を<xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>します。 `example3`文字列補間文字列を渡すことによってルール CA1305 を満たす<xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>します。

```csharp
string name = "Georgette";

// Violates CA1305
string example1 = String.Format("Hello {0}", name);

// Satisfies CA1305
string example2 = String.Format(CultureInfo.CurrentCulture, "Hello {0}", name);

// Satisfies CA1305
string example3 = FormattableString.Invariant($"Hello {name}");
```

## <a name="related-rules"></a>関連するルール

- [CA1304:CultureInfo を指定します](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>関連項目

- [CultureInfo クラスを使用します。](/dotnet/standard/globalization-localization/globalization#Cultures)