---
title: CA1408:AutoDual ClassInterfaceType を使用しないでください
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: df4cfcee306a70496d7e9b3487bd08853ffeb37a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54950560"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408:AutoDual ClassInterfaceType を使用しないでください

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 コンポーネント オブジェクト モデル (COM) 参照できる型が付いて、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性に設定、 `AutoDual` @property<xref:System.Runtime.InteropServices.ClassInterfaceType>します。

## <a name="rule-description"></a>規則の説明
 デュアル インターフェイスを使用する型を使用することで、クライアントを特定のインターフェイス レイアウトに対応付けることができます。 将来のバージョンで、この型またはその基本型のレイアウトに変更が加えられると、インターフェイスに対応付けられた COM クライアントが切り離されます。 既定では場合、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性が指定されていない、ディスパッチ専用インターフェイスが使用されます。

 それ以外の場合にマークされている場合は、すべてのパブリックの非ジェネリック型の COM; から参照できるものすべての非パブリックとジェネリック型が COM に表示されません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するには、値を変更、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性を`None`の値<xref:System.Runtime.InteropServices.ClassInterfaceType>し、明示的にインターフェイスを定義します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 特定の種類とその基本型のレイアウトが、今後のバージョンで変更されないことがない限り、この規則による警告を抑制しないでください。

## <a name="example"></a>例
 次の例では、規則に違反すると、明示的なインターフェイスを使用して、クラスの再宣言するクラスを示します。

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>関連するルール
 [CA 1403:Auto 配置の型が COM に表示することはできません。](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA 1412:ComSource インターフェイスを IDispatch として設定します](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>関連項目

- [要件 (相互運用のための .NET 型の)](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)