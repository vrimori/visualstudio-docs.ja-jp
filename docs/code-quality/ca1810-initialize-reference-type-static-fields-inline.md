---
title: 'CA1810: 参照型の静的フィールドをインラインで初期化します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b31a0bbea244d5d196364517b5c5a2ca8d7a53a1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: 参照型の静的フィールドをインラインで初期化します
|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 参照型では、明示的な静的コンス トラクターを宣言します。

## <a name="rule-description"></a>規則の説明
 型で明示的な静的コンストラクターを宣言すると、Just-In-Time (JIT) コンパイラが、静的コンストラクターが呼び出されたことを確認するために、型の静的メソッドと静的インスタンス コンストラクターに個別にチェックを追加します。 静的な初期化が静的メンバーにアクセスする場合、または型のインスタンスが作成されるときにトリガーされます。 ただし、型の変数を宣言は使用しないで、初期化には、グローバル状態が変更された場合に重要なこともある場合、静的な初期化はトリガーされません。

 すべての静的データはインラインで初期化し、明示的な静的コンス トラクターが宣言されていないときに、Microsoft intermediate language (MSIL) コンパイラが追加、`beforefieldinit`フラグと暗黙的な静的コンス トラクター、MSIL の型に、静的データを初期化します。定義です。 JIT コンパイラが検出した場合、`beforefieldinit`フラグ、ほとんどの場合は、静的コンス トラクターのチェックは追加されません。 静的な初期化は、静的メソッドまたはインスタンスのコンス トラクターが呼び出される前にありませんが、静的フィールドがアクセスされる前に、いくつかの時点で発生することが保証します。 静的な初期化は、いつでも、型の変数が宣言された後に発生する可能性が注意してください。

 静的コンストラクターのチェックによってパフォーマンスが低下することがあります。 多くの場合、静的コンス トラクターは、ケースだけは必ず静的な初期化が発生している静的フィールドの最初のアクセス前に、静的フィールドの初期化にのみ使用されます。 `beforefieldinit`動作に適したこれらおよび他のほとんどの型。 のみ適切でない静的な初期化がグローバル状態に影響し、次のいずれかが当てはまるときです。

-   グローバル状態への影響は、コストが、型を使用しない場合は必要ありません。

-   グローバル状態の結果は、型の静的フィールドにアクセスしなくてもアクセスできます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、静的データが宣言されたとき、および静的コンストラクターを削除するときに、静的データをすべて初期化します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 パフォーマンスが重要でない場合、この規則による警告を抑制しても安全です。型の静的メソッドが呼び出されるか、型のインスタンスを作成する前に発生する、またはかどうか静的な初期化によって引き起こされるグローバル状態の変更は手間がかかります必要がありますを保証します。

## <a name="example"></a>例
 次の例は、型`StaticConstructor`、ルールを型に違反する`NoStaticConstructor`規則に適合するインラインの初期化で、静的コンス トラクターを置き換えます。

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

 追加に注意してください、 `beforefieldinit` MSIL の定義のフラグ、`NoStaticConstructor`クラスです。

 **パブリック .class 自動 ansi StaticConstructor** **拡張 [mscorlib]System.Object**
 **{**
 **}/終了/クラス StaticConstructorの**
 **.class パブリック自動 ansi beforefieldinit NoStaticConstructor** **拡張 [mscorlib]System.Object**
 **{**
 **}/終了/クラス NoStaticConstructor の**
## <a name="related-rules"></a>関連規則
 [CA2207: 値型の静的フィールドのインラインを初期化します](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)