---
title: CA2119:プライベート インターフェイスを満たすメソッドをシールします
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 48fbe9e56c1286acc2eb948d0ec692f441bd1975
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920736"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119:プライベート インターフェイスを満たすメソッドをシールします

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 継承可能なパブリック型のオーバーライド可能なメソッド実装を提供する、 `internal` (`Friend` Visual Basic で) インターフェイス。

## <a name="rule-description"></a>規則の説明
 インターフェイス メソッドがあるパブリック アクセシビリティは、実装する型を変更できません。 内部のインターフェイスは、インターフェイスを定義するアセンブリの外側に実装されるものではありませんが、コントラクトを作成します。 使用して、内部のインターフェイスのメソッドを実装するパブリック型、 `virtual` (`Overridable` Visual basic) 修飾子は、アセンブリ外にある派生型でオーバーライドされるメソッドを使用します。 2 番目の型定義のアセンブリでは、メソッドを呼び出し、内部専用の契約が必要ですが場合、代わりに、外部のアセンブリでオーバーライドされたメソッドが実行されるときに、動作が漏えいする可能性があります。 これには、セキュリティの脆弱性が作成されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則の違反を修正するには、メソッドが、次のいずれかを使用して、アセンブリの外部にオーバーライドされないように。

- 宣言する型`sealed`(`NotInheritable` Visual Basic で)。

- 宣言する型のアクセシビリティを変更する`internal`(`Friend` Visual Basic で)。

- すべてのパブリック コンス トラクターを宣言する型から削除します。

- メソッドの実装を使用せず、`virtual`修飾子。

- メソッドを明示的に実装します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この警告を抑制するには、安全ではルールの場合、セキュリティの問題が存在しないことを注意深くレビューは、アセンブリの外部メソッドがオーバーライドされた場合に悪用可能な場合があります。

## <a name="example-1"></a>例 1
 次の例は、型`BaseImplementation`、この規則に違反します。

 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example-2"></a>例 2
 次の例では、前の例の仮想メソッドの実装を悪用します。

 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>関連項目

- [インターフェイス](/dotnet/csharp/programming-guide/interfaces/index)
- [インターフェイス](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)