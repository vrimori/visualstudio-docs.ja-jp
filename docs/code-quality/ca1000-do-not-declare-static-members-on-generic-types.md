---
title: CA1000:ジェネリック型の静的メンバーを宣言しません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f4f0a21f685cc4ff1edc54aa8002d6ecb3c28b9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890522"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000:ジェネリック型の静的メンバーを宣言しません

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照のジェネリック型が含まれています、 `static` (`Shared` Visual Basic で) メンバー。

## <a name="rule-description"></a>規則の説明
 ときに、`static`ジェネリック型のメンバーが呼び出されると、型に対して型引数を指定する必要があります。 推論をサポートしないジェネリック インスタンス メンバーを呼び出すときには、そのメンバーに型引数を指定する必要があります。 これら 2 つの場合、型引数を指定する構文では、異なるが、混同、次の呼び出しが示すようには。

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

 一般に、型引数が、メンバーを呼び出すときに指定する必要があるないように、この両方の以前の宣言を回避する必要があります。 これにより、構文での非ジェネリックの構文の違いもなく、ジェネリック型のメンバーを呼び出すことです。 詳細については、次を参照してください。 [ca 1004。ジェネリック メソッドは、型パラメーターを指定する必要があります](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、静的メンバーを削除またはインスタンス メンバーを変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。 ジェネリックでは簡単に理解して使用する構文を提供するには、習得に必要なされ、新しいライブラリの導入速度を向上する時間が短縮されます。

## <a name="related-rules"></a>関連するルール
 [CA1005:ジェネリック型で過剰なパラメーターを回避します。](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA 1010:コレクションは、ジェネリック インターフェイスを実装する必要があります。](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA 1002:ジェネリック リストを公開しません](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA 1006:ジェネリック型メンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA 1004:ジェネリック メソッドは、型パラメーターを指定する必要があります。](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA 1003:汎用イベント ハンドラーのインスタンスを使用して、](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA 1007:適切な場所にジェネリックを使用します。](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>関連項目
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)