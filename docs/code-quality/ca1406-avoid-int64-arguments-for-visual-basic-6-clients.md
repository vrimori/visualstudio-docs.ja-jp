---
title: ': Ca 1406 Visual Basic 6 クライアントに対しては Int64 引数 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.workload:
- multiple
ms.openlocfilehash: 3b07be7368269701b2b77fa633464095cc509779
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Visual Basic 6 クライアントに対しては Int64 引数を使用しません
|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|カテゴリ|Microsoft.Interoperability|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 コンポーネント オブジェクト モデル (COM) を参照できると明確にマークされている型はメンバーを行うためにかかる宣言、<xref:System.Int64?displayProperty=fullName>引数。  
  
## <a name="rule-description"></a>規則の説明  
 Visual Basic 6 COM クライアントは、64 ビット整数値にアクセスできません。  
  
 既定では、次が COM 参照可能な: アセンブリ、パブリックな型、パブリック型は、パブリック インスタンス メンバーおよびパブリック値型のすべてのメンバーです。 ただし、偽陽性を減らすためには、この規則が必要、COM 型の可視性、明示的に指定します。格納しているアセンブリをマークする必要があります、 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 'éý'`false`で型をマークする必要がありますと、 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 'éý'`true`です。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 パラメーターの値を持つを 32 ビット整数として表すことが常にこの規則違反を修正するには、変更するパラメーターの型を<xref:System.Int32?displayProperty=fullName>です。 パラメーターの型を変更する場合は、パラメーターの値は、32 ビット整数として表現できるよりも大きい場合がある、<xref:System.Decimal?displayProperty=fullName>です。 なお両方<xref:System.Single?displayProperty=fullName>と<xref:System.Double?displayProperty=fullName>の範囲の上限で精度が失われる、<xref:System.Int64>データ型。 場合は、メンバーは、COM から参照できるものではありません、使用してマークする、 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 'éý'`false`です。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 Visual Basic 6 COM クライアントは、型をアクセスしていないことが確実である場合にこの規則による警告を抑制しても安全です。  
  
## <a name="example"></a>例  
 次の例は、規則に違反する型を示しています。  
  
 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Com 参照可能な型で静的メンバーを使用しません](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>関連項目  
 [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)   
 [Long データ型](/dotnet/visual-basic/language-reference/data-types/long-data-type)