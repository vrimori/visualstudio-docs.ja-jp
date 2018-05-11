---
title: 'CA1405: COM 参照可能な型の基本型は COM 参照可能でなければなりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1eefb3fdb207ecacca4998168509e8c5b9b1a2f1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: COM 参照可能な型の基本型は COM 参照可能でなければなりません
|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|DependsOnFix|

## <a name="cause"></a>原因
 コンポーネント オブジェクト モデル (COM) 参照できる型は、COM 参照可能ではない型から派生します。

## <a name="rule-description"></a>規則の説明
 COM 参照可能な型では、新しいバージョンのメンバーを追加、ときに、現在のバージョンにバインドする COM クライアントを破損しないようにする厳密なガイドラインに従う必要があります。 COM に表示される種類は、新しいメンバーを追加したときに COM バージョン管理規則に従う必要はありませんを開始します。 場合は COM 参照可能型の COM の非表示の型から派生し、クラス インターフェイスの公開<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName>または<xref:System.Runtime.InteropServices.ClassInterfaceType>(既定) の場合、基本型のすべてのパブリック メンバー (具体的にとしてマークされている COM 非表示、しない限り、れる冗長)COM に公開されます。 基本データ型は、それ以降のバージョンに新しいメンバーを追加する場合は、派生型のクラスのインターフェイスに関連付けているすべての COM クライアントが壊れる可能性があります。 COM 参照可能な型は、COM クライアントを中断する可能性を低減する COM 参照可能な型からのみ派生する必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、COM 参照の基本型または派生型を COM を非表示にします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例は、規則に違反する型を示しています。

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>関連項目
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)