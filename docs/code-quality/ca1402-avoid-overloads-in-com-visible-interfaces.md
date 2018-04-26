---
title: 'CA1402: COM 参照可能インターフェイスでのオーバーロードを避けてください'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.workload:
- multiple
ms.openlocfilehash: ec1e0f13d3d26973dc2dc46c6a41a2dc962c91bb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: COM 参照可能インターフェイスでのオーバーロードを避けてください
|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 オーバー ロードされたメソッドのコンポーネント オブジェクト モデル (COM) 参照できるインターフェイスを宣言します。

## <a name="rule-description"></a>規則の説明
 オーバーロードされたメソッドが COM クライアントに公開されると、最初のメソッド オーバーロードだけが名前を保持します。 後続のオーバー ロードは一意に名前にアンダー スコア文字 '_' とオーバー ロードの宣言の順序に対応する整数を追加して名前を変更します。 たとえば、次の方法を検討してください。

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 これらのメソッドは、次のように COM クライアントに公開されます。

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 Visual Basic 6 COM クライアントは、名前にアンダー スコアを使用して、インターフェイス メソッドを実装することはできません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、名前が一意になるため、オーバー ロードされたメソッドの名前を変更します。 またへのアクセシビリティを変更することで、インターフェイスが COM に非表示こと`internal`(`Friend`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) または適用することによって、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>属性に設定`false`です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、この規則に違反するインターフェイスと規則に適合するインターフェイスを示します。

 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Com 参照可能な型で静的メンバーを使用しません](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>関連項目
 [アンマネージ コードと相互運用](/dotnet/framework/interop/index) [Long データ型](/dotnet/visual-basic/language-reference/data-types/long-data-type)