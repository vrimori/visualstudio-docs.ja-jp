---
title: 'CA1013: オーバーロードする加算および減算で、演算子 equals をオーバーロードします'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11841248192bc9b726076641e1219f54ab526447
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31897432"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: オーバーロードする加算および減算で、演算子 equals をオーバーロードします
|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 パブリック型またはプロテクト型で、等値演算子を実装しないまま、加算演算子または減算演算子を実装しています。

## <a name="rule-description"></a>規則の説明
 等しいかどうかを返す必要がありますほとんどの場合を定義する型のインスタンスは、加算や減算などの操作を使用して組み合わせることができます、`true`同じ構成値を持つ 2 つのインスタンス。

 等値演算子のオーバー ロードされた実装では、既定の等値演算子を使用できません。 こうと、スタック オーバーフローが発生します。 等値演算子を実装するのには、実装で、Object.Equals メソッドを使用します。 次の例を参照してください。

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、加算と減算演算子と数学的に一貫したように、等値演算子を実装します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 等値演算子の既定の実装が正常に動作の型を提供する場合は、この規則による警告を抑制しても安全です。

## <a name="example"></a>例
 次の例は、型を定義 (`BadAddableType`) この規則に違反します。 この型は、テスト同じフィールドの値を持つ 2 つのインスタンスに等値演算子を実装する必要があります`true`等しいかどうか。 型`GoodAddableType`修正の実装を示しています。 この型も非等値演算子を実装して上書き<xref:System.Object.Equals%2A>を他のルールを満たすためにします。 完全な実装に使用する場合<xref:System.Object.GetHashCode%2A>です。

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>例
 次の例は、等値演算子の既定値と正しい動作を説明するためには、このトピックで以前に定義されている型のインスタンスを使用して、等しいかどうかテストします。

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

 この例を実行すると、次の出力が生成されます。

 **不適切な型: {2,2} {2,2}が等しいか?いいえ**
**適切な型: {3,3} {3,3}が等しいか?[はい]**
**適切な型: {3,3} {3,3}は、= = しますか? [はい]**
**不適切な型: {2,2} {9,9}が等しいか?いいえ**
**適切な型: {3,3} {9,9}は、= = しますか? 違います**
## <a name="see-also"></a>関連項目
 [等値演算子](/dotnet/standard/design-guidelines/equality-operators)