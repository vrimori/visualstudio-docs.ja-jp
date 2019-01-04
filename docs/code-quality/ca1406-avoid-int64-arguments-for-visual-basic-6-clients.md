---
title: CA1406:Visual Basic 6 クライアントに対しては Int64 引数を使用しません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6d39c98aae5ae577ad82f0ff99f1069fb34e5146
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920940"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406:Visual Basic 6 クライアントに対しては Int64 引数を使用しません

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 コンポーネント オブジェクト モデル (COM) を参照できると明確にマークされている型はそのがのメンバーを宣言して、<xref:System.Int64?displayProperty=fullName>引数。

## <a name="rule-description"></a>規則の説明
 Visual Basic 6 COM クライアントは、64 ビット整数値にアクセスできません。

 既定では、次は COM から参照できる: アセンブリ、型のパブリック、パブリック型は、パブリック インスタンス メンバーおよびパブリック値型のすべてのメンバー。 ただし、偽陽性を減らすためには、このルールが必要です。 明示的に指定する対象の型の COM の参照範囲格納しているアセンブリをマークする必要があります、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>に設定`false`で型をマークする必要があり、<xref:System.Runtime.InteropServices.ComVisibleAttribute>に設定`true`します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 パラメーターの値を持つを 32 ビット整数として表すことが常にこの規則の違反を修正するには、パラメーターの型を変更する<xref:System.Int32?displayProperty=fullName>します。 パラメーターの型を変更する場合は、パラメーターの値は、32 ビット整数として表すことがよりも大きい可能性があります、<xref:System.Decimal?displayProperty=fullName>します。 なお両方<xref:System.Single?displayProperty=fullName>と<xref:System.Double?displayProperty=fullName>の範囲で精度が失われる、<xref:System.Int64>データ型。 メンバーは、COM に表示されるものではない場合に、そのマーク、<xref:System.Runtime.InteropServices.ComVisibleAttribute>設定`false`します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 Visual Basic 6 COM クライアントは、型をアクセスしていないことが確実である場合は、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例では、規則に違反する型を示します。

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>関連するルール
 [CA1413:COM 参照可能な値の型で非パブリック フィールドを回避します。](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407:COM 参照可能な型で静的メンバーを回避します。](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA 1017:アセンブリに comvisibleattribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>関連項目

- [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)
- [Long データ型](/dotnet/visual-basic/language-reference/data-types/long-data-type)