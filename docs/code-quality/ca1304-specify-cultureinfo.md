---
title: 'CA1304: CultureInfo を指定します'
ms.date: 11/04/2016
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
ms.openlocfilehash: dec38172f65b7b4d828dc96f0b2f51b28ce1ebd6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: CultureInfo を指定します
|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 メソッドまたはコンス トラクターを受け入れるオーバー ロードを持つメンバーを呼び出して、<xref:System.Globalization.CultureInfo?displayProperty=fullName>パラメーター、およびメソッドまたはコンス トラクターは使用するオーバー ロードを呼び出しません、<xref:System.Globalization.CultureInfo>パラメーター。 このルールは、次のメソッドの呼び出しを無視します。

-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>規則の説明
 ときに、<xref:System.Globalization.CultureInfo>または<xref:System.IFormatProvider?displayProperty=fullName>オブジェクトが指定されていない、オーバー ロードされたメンバーから提示された既定値を目的の効果をすべてのロケールでない可能性があります。 また、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]メンバーの既定のカルチャを選択して、コードに対して正しいことができない可能性がある前提条件に基づく書式設定します。 コードの場合で期待どおりに動作させるには、次のガイドラインに従ってカルチャに固有の情報を指定する必要があります。

-   場合は、値は、ユーザーに表示されますが、現在のカルチャを使用します。 「<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>」を参照してください。

-   場合は、値が格納され、ソフトウェアによってアクセスされる、ファイルまたはデータベースに保持される使用して、インバリアント カルチャ。 「<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>」を参照してください。

-   値のコピー先がわからない場合は、データ コンシューマーがあるか、プロバイダーがカルチャを指定します。

 なお<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>のインスタンスを使用して、ローカライズされたリソースを取得する場合のみ使用される、<xref:System.Resources.ResourceManager?displayProperty=fullName>クラスです。

 オーバー ロードされたメンバーの既定の動作がニーズに適した場合でも、コードが自己文書化し、保守を容易にするために、カルチャに固有のオーバー ロードを明示的に呼び出すことをお勧めします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、使用するオーバー ロードを使用して、<xref:System.Globalization.CultureInfo>または<xref:System.IFormatProvider>し、以前に一覧表示するガイドラインに従って引数を指定します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 コードの保守性が重要な開発の優先順位ではない、既定のカルチャまたは書式プロバイダーが、適切な選択であるが確実であるときにこの規則による警告を抑制しても安全です。

## <a name="example"></a>例
 次の例では、`BadMethod`によりこの規則の 2 つ違反が発生します。 `GoodMethod` System.String.Compare にインバリアント カルチャを渡すことによって最初の違反を修正し、現在のカルチャを渡すことによって、2 番目の違反を修正<xref:System.String.ToLower%2A>ため`string3`がユーザーに表示されます。

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example"></a>例
 次の例は、既定の現在のカルチャの効果を示します<xref:System.IFormatProvider>で選択されている、<xref:System.DateTime>型です。

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

 この例を実行すると、次の出力が生成されます。

 **1900 年 6 月 4 日 12時 15分: 12 PM**
**06/04/1900 12時 15分: 12**
## <a name="related-rules"></a>関連規則
 [CA1305: IFormatProvider を指定します](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>関連項目
[CultureInfo クラスを使用します。](/dotnet/standard/globalization-localization/globalization#Cultures)