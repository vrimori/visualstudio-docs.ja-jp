---
title: CA2214:コンストラクターのオーバーライド可能なメソッドを呼び出しません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 99f0877e0dea9876f8c708106a64a70e194bd9d0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017202"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214:コンストラクターのオーバーライド可能なメソッドを呼び出しません

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

封印されていない型のコンス トラクターは、そのクラスで定義されている仮想メソッドを呼び出します。

## <a name="rule-description"></a>規則の説明

仮想メソッドが呼び出されると、実行時までは、メソッドを実行する実際の型が選択されていません。 コンス トラクターは、仮想メソッドを呼び出し、メソッドを呼び出すインスタンスのコンス トラクターが実行しないことになります。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するには、型のコンス トラクター内からに型の仮想メソッドを呼び出す操作を行います。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。 コンス トラクターは、仮想メソッド呼び出しを削除して再設計する必要があります。

## <a name="example"></a>例

次の例では、この規則違反の効果を示します。 テスト アプリケーションのインスタンスを作成する`DerivedType`、それが原因で、基底クラス (`BadlyConstructedType`) コンス トラクターが実行されます。 `BadlyConstructedType`コンス トラクターが仮想メソッドを正しく呼び出します`DoSomething`します。 出力を`DerivedType.DoSomething()`を実行して、前に`DerivedType`のコンス トラクターを実行します。

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

この例を実行すると、次の出力が生成されます。

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```