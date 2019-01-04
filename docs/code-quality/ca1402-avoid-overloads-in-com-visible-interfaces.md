---
title: CA1402:COM 参照可能インターフェイスでのオーバーロードを避けてください
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 056e572ef7a572c83731851d49420e0c713c6cc9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935529"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402:COM 参照可能インターフェイスでのオーバーロードを避けてください

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 オーバー ロードされたメソッドのコンポーネント オブジェクト モデル (COM) 参照できるインターフェイスを宣言します。

## <a name="rule-description"></a>規則の説明
 オーバーロードされたメソッドが COM クライアントに公開されると、最初のメソッド オーバーロードだけが名前を保持します。 後続のオーバー ロードが名前にアンダー スコア文字 '_' とオーバー ロードの宣言の順序に対応する整数を追加して一意に変更されます。 たとえば、次の方法を検討してください。

```csharp
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

これらのメソッドは、次のように COM クライアントに公開されます。

```csharp
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

Visual Basic 6 COM クライアントは、名前にアンダー スコアを使用して、インターフェイス メソッドを実装することはできません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、名前が一意になるため、オーバー ロードされたメソッドの名前を変更します。 またへのアクセシビリティを変更することで、インターフェイスが COM に非表示こと`internal`(`Friend`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) または適用することで、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>属性に設定`false`します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、インターフェイス、規則に違反して、規則に適合するインターフェイスを示します。

 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## <a name="related-rules"></a>関連するルール
 [CA1413:COM 参照可能な値の型で非パブリック フィールドを回避します。](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407:COM 参照可能な型で静的メンバーを回避します。](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA 1017:アセンブリに comvisibleattribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>関連項目

- [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)
- [Long データ型](/dotnet/visual-basic/language-reference/data-types/long-data-type)