---
title: 'Ca 1810: 参照型の静的フィールド インラインで初期化 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e4d7ffbe4fc821ffd70b0bb299b2a4738d63873b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862685"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: 参照型の静的フィールドをインラインで初期化します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 参照型では、明示的な静的コンス トラクターを宣言します。

## <a name="rule-description"></a>規則の説明
 型で明示的な静的コンストラクターを宣言すると、Just-In-Time (JIT) コンパイラが、静的コンストラクターが呼び出されたことを確認するために、型の静的メソッドと静的インスタンス コンストラクターに個別にチェックを追加します。 静的な初期化は、任意の静的メンバーにアクセスする場合、または型のインスタンスが作成されたときにトリガーされます。 ただし、型の変数を宣言するが、それを使用しない、初期化には、グローバル状態が変更された場合に重要なこともある場合、静的な初期化はトリガーされません。

 すべての静的データが初期化されたインラインと明示的な静的コンス トラクターが宣言されていない、Microsoft intermediate language (MSIL) コンパイラが追加、`beforefieldinit`フラグと暗黙的な静的コンス トラクター、静的データ、MSIL の型を初期化します。定義。 JIT コンパイラが検出した場合、`beforefieldinit`フラグ、ほとんどの場合、静的コンス トラクターのチェックは追加されません。 静的な初期化を静的メソッドまたはインスタンスのコンス トラクターが呼び出される前にありませんが、静的フィールドにアクセスする前に、いくつかの時点で発生することが保証されます。 静的な初期化が型の変数が宣言された後にいつでも行うことができますに注意してください。

 静的コンストラクターのチェックによってパフォーマンスが低下することがあります。 多くの場合、静的コンス トラクターは、静的フィールドの最初のアクセスする前にする必要がありますのみを確認する静的な初期化ケースが発生する静的フィールドの初期化にのみ使用されます。 `beforefieldinit`な場合、これらおよびその他のほとんどの種類。 適切でないのみ静的な初期化がグローバルな状態に影響し、次のいずれかが当てはまるときです。

-   グローバル状態への影響は、コストが、型を使用しない場合は必要ありません。

-   グローバル状態の結果は、型の静的フィールドにアクセスしなくてもアクセスできます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、静的データが宣言されたとき、および静的コンストラクターを削除するときに、静的データをすべて初期化します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 パフォーマンスが重要でない場合は、この規則による警告を抑制するのには安全では型の静的メソッドが呼び出されるか、型のインスタンスを作成する前に発生するかどうかの静的な初期化によって引き起こされるグローバル状態の変更が高価なかする必要がありますまたはを保証します。

## <a name="example"></a>例
 次の例は、型`StaticConstructor`、ルールと、型に違反する`NoStaticConstructor`ルールを満たすためにインライン初期化で、静的コンス トラクターを置き換えます。

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 メモの追加、`beforefieldinit`フラグの定義を MSIL を`NoStaticConstructor`クラス。

 **パブリック .class auto ansi StaticConstructor** **拡張 [mscorlib]System.Object**
 **{**
 **}/終了/StaticConstructorクラスの**
 **.class パブリック自動 ansi beforefieldinit NoStaticConstructor** **拡張 [mscorlib]System.Object**
 **{**
 **}/終了/NoStaticConstructor クラスの**
## <a name="related-rules"></a>関連規則
 [CA2207: 値型の静的フィールドのインラインを初期化します](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)



