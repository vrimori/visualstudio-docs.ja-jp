---
title: 'CA2214: コンストラクターのオーバーライド可能なメソッドを呼び出しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5ebcd4164f9db28d4cb1f150ee3a4bb21b21cde
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: コンストラクターのオーバーライド可能なメソッドを呼び出しません
|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 封印されていない型のコンス トラクターは、そのクラスで定義されている仮想メソッドを呼び出します。

## <a name="rule-description"></a>規則の説明
 仮想メソッドが呼び出されると、実行時までは、メソッドを実行する実際の型が選択されていません。 コンス トラクターが仮想メソッドを呼び出すと、そのメソッドを呼び出すインスタンスのコンス トラクターが実行していないことができます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するのには、型のコンス トラクター内からの型の仮想メソッドの呼び出す必要はありません。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 仮想メソッドの呼び出しを回避するのには、コンス トラクターを再設計する必要があります。

## <a name="example"></a>例
 次の例では、この規則違反の影響を示します。 テスト アプリケーションのインスタンスを作成する`DerivedType`、それが原因で、基本クラス (`BadlyConstructedType`) コンス トラクターが実行されます。 `BadlyConstructedType`コンス トラクターが、仮想メソッドを正しく呼び出す`DoSomething`です。 出力に示す`DerivedType.DoSomething()`が実行され、前に`DerivedType`のコンス トラクターを実行します。

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

 この例を実行すると、次の出力が生成されます。

 **基本 ctor を呼び出しています。** 
 **DoSomething の派生には、呼び出される初期化ですか?いいえ**
**通話が ctor を派生します。**