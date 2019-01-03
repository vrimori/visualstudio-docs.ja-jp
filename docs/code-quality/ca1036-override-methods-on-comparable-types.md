---
title: CA1036:比較可能な型でメソッドをオーバーライドします
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 05f4bd750f1ec2ad4d336acb1a00b8848de389bf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825582"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036:比較可能な型でメソッドをオーバーライドします

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型を実装、<xref:System.IComparable?displayProperty=fullName>インターフェイスをオーバーライドしない<xref:System.Object.Equals%2A?displayProperty=fullName>または等しいかどうか、非等値、言語固有の演算子が小さいオーバー ロードできません- か、大きい-よりもします。 ルールは、型がインターフェイスの実装のみを継承する場合、違反を報告しません。

## <a name="rule-description"></a>規則の説明

カスタムの並べ替え順序を定義する型を実装、<xref:System.IComparable>インターフェイス。 <xref:System.IComparable.CompareTo%2A>メソッドは、型の 2 つのインスタンスの正しい並べ替え順序を示す整数値を返します。 このルールは、並べ替え順序を設定する型を識別します。 並べ替え順序を設定することを意味等しいかどうかの通常の意味、非等値、-、およびそれ以降-よりは適用されません。 実装を提供する<xref:System.IComparable>、通常必要がありますもオーバーライド<xref:System.Object.Equals%2A>と一致する値を返すように<xref:System.IComparable.CompareTo%2A>します。 オーバーライドする場合は<xref:System.Object.Equals%2A>コーディングと演算子のオーバー ロードをサポートする言語に合致する演算子も提供する必要があります<xref:System.Object.Equals%2A>します。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには、オーバーライド<xref:System.Object.Equals%2A>します。 使用するプログラミング言語では、演算子のオーバー ロードをサポートする場合は、次の演算子を指定します。

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

C# でこれらの演算子を表すために使用されるトークンは次のとおりです。

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 Ca 1036 演算子と、プログラミング言語がないために、違反が発生する場合が演算子のオーバー ロードをサポートしていません Visual Basic の場合と同様のルールから警告を抑制しても安全です。 Op_Equality 演算子を実装するいると判断した場合は、アプリケーションのコンテキストで意味を成しません以外の等値演算子を発生させるときにこの規則からの警告を抑制しても安全です。 ただしは常に op_Equality 経由で、Object.Equals をオーバーライドする場合は、演算子を = =。

## <a name="example"></a>例
 次の例には、正しく実装する型が含まれています。<xref:System.IComparable>します。 コードのコメントを関連するさまざまなルールを満たすメソッドを識別する<xref:System.Object.Equals%2A>と<xref:System.IComparable>インターフェイス。

 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

## <a name="example"></a>例
 次のアプリケーションの動作をテストする、<xref:System.IComparable>前に示した実装します。

 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>関連項目

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [等値演算子](/dotnet/standard/design-guidelines/equality-operators)