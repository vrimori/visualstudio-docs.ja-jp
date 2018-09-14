---
title: 'CA1409: COM 参照可能な型は作成可能でなければなりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 817c2215245412faf0bb30d46aec40a953f239b5
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546851"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: COM 参照可能な型は作成可能でなければなりません

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 コンポーネント オブジェクト モデル (COM) を参照できると明確にマークされている参照型では、パブリックのパラメーター化されたコンス トラクターが含まれていますが、(パラメーターなしの) パブリックの既定のコンス トラクターが含まれていません。

## <a name="rule-description"></a>規則の説明
 COM クライアントでは、パブリックの既定のコンス トラクターのない型を作成できません。 ただし、種類もアクセスできます COM クライアントで別の手段の種類を作成し (たとえば、メソッド呼び出しの戻り値) を使用してクライアントに渡すことがある場合。

 派生した型を規則<xref:System.Delegate?displayProperty=fullName>します。

 既定では、次は COM から参照できる: アセンブリ、型のパブリック、パブリック型は、パブリック インスタンス メンバーおよびパブリック値型のすべてのメンバー。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、既定のパブリック コンス トラクターを追加または削除、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>型から。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 COM クライアントを作成し、オブジェクトを他の方法が提供されている場合は、この規則による警告を抑制するのには安全です。

## <a name="related-rules"></a>関連するルール
 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>関連項目

- [要件 (相互運用のための .NET 型の)](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)