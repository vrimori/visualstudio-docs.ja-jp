---
title: '1305: IFormatProvider を指定 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 107248d0dddf89f63056a8a385eeb2a942ca91c8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186705"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: IFormatProvider を指定します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 メソッドまたはコンス トラクターの呼び出しを受け入れるオーバー ロードを持つ 1 つまたは複数のメンバー、<xref:System.IFormatProvider?displayProperty=fullName>パラメーター、およびメソッドまたはコンス トラクターは使用するオーバー ロードを呼び出しません、<xref:System.IFormatProvider>パラメーター。 このルールの呼び出しを無視する[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]無視として説明されているメソッド、<xref:System.IFormatProvider>パラメーターと、さらに次のメソッド。

-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>規則の説明
 ときに、<xref:System.Globalization.CultureInfo?displayProperty=fullName>または<xref:System.IFormatProvider>オブジェクトが指定されていない、オーバー ロードされたメンバーによって提供される既定値はすべてのロケールに効果がありません。 また、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]メンバーが既定のカルチャを選択し、コードの適切なことができない可能性がある前提条件に基づく書式設定します。 コードが、シナリオのために期待どおりに動作することを確認するには、次のガイドラインに従って、カルチャに固有の情報を指定する必要があります。

-   場合は、値は、ユーザーに表示されますが、現在のカルチャを使用します。 以下を参照してください。<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>

-   値が格納され、ソフトウェア (ファイルまたはデータベースに保存される) からアクセスされる場合、は、インバリアント カルチャを使用します。 以下を参照してください。<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>

-   値の変換先がわからない場合は、データ コンシューマーがあるか、プロバイダーが、カルチャを指定します。

 なお<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>のインスタンスを使用して、ローカライズされたリソースを取得するためだけに使用、<xref:System.Resources.ResourceManager?displayProperty=fullName>クラス。

 オーバー ロードされたメンバーの既定の動作がニーズに適した場合でもを明示的にされるため、コードを自己文書化して保守が簡単なカルチャ固有のオーバー ロードを呼び出すことをお勧めします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するを受け取るオーバー ロードを使用して、<xref:System.Globalization.CultureInfo>または<xref:System.IFormatProvider>し上記で示したガイドラインに従って引数を指定します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 既定のカルチャまたは書式プロバイダーは、適切な選択とコードの保守性が重要な開発の優先順位ではないことが確実である場合にこの規則による警告を安全になります。

## <a name="example"></a>例
 次の例では、`BadMethod`によりこの規則の違反が 2 つ発生します。 `GoodMethod` インバリアント カルチャを渡すことによって、最初の違反を修正<xref:System.String.Compare%2A>には、現在のカルチャを渡すことによって、2 つ目の違反を修正し、<xref:System.String.ToLower%2A>ため`string3`がユーザーに表示されます。

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>例
 次の例では、既定値に対する現在のカルチャの効果を示します<xref:System.IFormatProvider>によって選択されている、<xref:System.DateTime>型。

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **1900 年 6 月 4/12時 15分: 12 PM**
**06/04/1900 12時 15分: 12**
## <a name="related-rules"></a>関連規則
 [CA1304: CultureInfo を指定します](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>関連項目
 [NIB: CultureInfo クラスの使用](http://msdn.microsoft.com/en-us/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)



