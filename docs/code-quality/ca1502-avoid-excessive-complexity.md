---
title: 'CA1502: メソッドの実装を複雑にしすぎないでください'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a532207bf8e002dbde92bb85115c35b4de954c48
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: メソッドの実装を複雑にしすぎないでください
|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|カテゴリ|Microsoft.Maintainability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 メソッドの名前がサイクロマティック複雑です。

## <a name="rule-description"></a>規則の説明
 *サイクロマティック複雑度*線形独立の条件付き分岐の複雑さと数によって決定されるメソッド経路数を計測します。 低のサイクロマティック複雑では、理解、テスト、および保守しやすい方法通常を示します。 サイクロマティック複雑度は、メソッドの制御フロー グラフから計算され、次のように指定します。

 サイクロマティック複雑度端のノードの数は + 1 の数を =

 ノードが、論理的な分岐ポイントとエッジを表すノードの間に行を表します。

 ルールは、サイクロマティック複雑度が 25 以上の違反を報告します。

 コード メトリックに関する詳細については、[複雑性の測定とマネージ コードの保守容易性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)、

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、サイクロマティック複雑度を減らすための方法をリファクターします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 複雑さを簡単に低下させることはできず、メソッドを簡単に理解して、テスト、および保守場合は、この規則による警告を抑制しても安全です。 特に、大規模なを含むメソッド`switch`(`Select`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ステートメントは、除外の対象です。 コード ベースで以前にリリース済みのコードでのランタイム動作の予期しない変更を導入したり、開発サイクル遅延は、コードのリファクタリングの保守容易性のメリットを上回る場合がありますが不安定になるリスクです。

## <a name="how-cyclomatic-complexity-is-calculated"></a>サイクロマティック複雑度を計算する方法
 サイクロマティック複雑度は、次に 1 を加算して計算されます。

-   分岐の数 (など`if`、 `while`、および`do`)

-   数`case`内のステートメント、 `switch`

 次の例では、さまざまなサイクロマティック複雑な作業の方法を示します。

## <a name="example"></a>例
 **1 のサイクロマティック複雑度**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]

## <a name="example"></a>例
 **2 のサイクロマティック複雑度**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]

## <a name="example"></a>例
 **3 のサイクロマティック複雑度**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]

## <a name="example"></a>例
 **8 のサイクロマティック複雑度**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]

## <a name="related-rules"></a>関連規則
 [CA1501: 継承を使用しすぎないでください](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>関連項目
 [マネージ コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)