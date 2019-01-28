---
title: CA1405:COM 参照可能な型の基本型は COM 参照可能でなければなりません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a94654475432706592c3cd2845488163529ca260
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943222"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405:COM 参照可能な型の基本型は COM 参照可能でなければなりません

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|DependsOnFix|

## <a name="cause"></a>原因
 コンポーネント オブジェクト モデル (COM) 参照できる型は、COM 参照可能でない型から派生します。

## <a name="rule-description"></a>規則の説明
 COM から参照できる型では、新しいバージョンのメンバーを追加、ときに、現在のバージョンにバインドされた COM クライアントが壊れないように厳密なガイドラインに従う必要があります。 COM から参照できる型では、COM のバージョン管理規則に従うと、新しいメンバーを追加する必要はありませんが前提としています。 場合は、COM 参照可能型は COM の非表示の型から派生しのクラス インターフェイスを公開<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName>または<xref:System.Runtime.InteropServices.ClassInterfaceType>(既定)、基本型のすべてのパブリック メンバー (専用としてマークされている COM 非表示をしない限り、このことは不要)COM に公開されます。 基本データ型は、以降のバージョンで新しいメンバーを追加する場合は、派生型のクラス インターフェイスにバインドされた COM クライアントが壊れる可能性があります。 COM 参照可能な型は、COM クライアントの可能性を低減する COM 参照可能な型からのみ派生する必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、基本型を COM 参照可能または派生型を COM を非表示にします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、規則に違反する型を示します。

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)