---
title: CA1413:Com 参照可能な値型ではパブリックでないフィールドを使用しません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 78152c3ee5825c34ea47e2267370720e698212dc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996468"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413:Com 参照可能な値型ではパブリックでないフィールドを使用しません

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 コンポーネント オブジェクト モデル (COM) を参照できると明確にマークされている値の型は、非パブリック インスタンス フィールドを宣言します。

## <a name="rule-description"></a>規則の説明
 COM から参照できる値型の非パブリック インスタンス フィールドは、COM クライアントで表示できます。 情報を公開してはなりません、または意図しないデザインまたはセキュリティ効果が含まれてのフィールドの内容を確認します。

 既定では、すべてのパブリック値型が COM から参照 ただし、偽陽性を減らすためには、この規則を明示的に指定する型の COM の参照範囲が必要です。 格納しているアセンブリをマークする必要があります、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>に設定`false`で型をマークする必要があり、<xref:System.Runtime.InteropServices.ComVisibleAttribute>に設定`true`します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 非表示フィールドの変更にこの規則の違反を修正するには、参照型に値の型を変更または削除、<xref:System.Runtime.InteropServices.ComVisibleAttribute>型からの属性。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 フィールドをパブリックに公開が許容される場合は、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例では、規則に違反する型を示します。

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>関連するルール
 [CA1407:COM 参照可能な型で静的メンバーを回避します。](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA 1017:アセンブリに comvisibleattribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>関連項目

- [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)
- [要件 (相互運用のための .NET 型の)](/dotnet/framework/interop/qualifying-net-types-for-interoperation)