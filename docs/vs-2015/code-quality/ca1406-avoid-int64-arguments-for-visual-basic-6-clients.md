---
title: ': Ca 1406 Visual Basic 6 クライアントに対しては Int64 引数 |Microsoft Docs'
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
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6976b1fc044aa488b0151dd28e459a870743bb13
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180090"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Visual Basic 6 クライアントに対しては Int64 引数を使用しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 Visual Basic 6 COM クライアントは、型をアクセスしていないことが確実である場合は、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例では、規則に違反する型を示します。

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Com 参照可能な型で静的メンバーを使用しません](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>関連項目
 [アンマネージ コードと相互運用](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Long データ型](http://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)



