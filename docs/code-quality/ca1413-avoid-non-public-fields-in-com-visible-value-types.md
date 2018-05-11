---
title: 'CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 170f4936258383cf26ed1d22fc78962b8b25e79c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません
|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 コンポーネント オブジェクト モデル (COM) を参照できると明確にマークされている値の型では、非パブリック インスタンス フィールドを宣言します。

## <a name="rule-description"></a>規則の説明
 COM から参照できる値型の非パブリック インスタンス フィールドは、COM クライアントで表示できます。 ない公開するべきで、または意図しない設計またはセキュリティ効果が含まれてについては、フィールドの内容を確認します。

 既定では、すべてのパブリック値型は COM に表示されます。 ただし、偽陽性を減らすためには、この規則を明示的に指定する型の COM の参照範囲が必要です。 格納しているアセンブリをマークする必要があります、 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 'éý'`false`で型をマークする必要がありますと、 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 'éý'`true`です。

## <a name="how-to-fix-violations"></a>違反の修正方法
 フィールドを非表示の変更にこの規則違反を修正するには、参照型に値の型を変更または削除、<xref:System.Runtime.InteropServices.ComVisibleAttribute>型からの属性です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制するフィールドをパブリックに公開が許容される場合にも安全です。

## <a name="example"></a>例
 次の例は、規則に違反する型を示しています。

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>関連規則
 [CA1407: Com 参照可能な型で静的メンバーを使用しません](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>関連項目
 [アンマネージ コードと相互運用](/dotnet/framework/interop/index)[相互運用のための .NET 型の条件を満たす](/dotnet/framework/interop/qualifying-net-types-for-interoperation)