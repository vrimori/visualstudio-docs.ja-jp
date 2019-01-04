---
title: CA1502:メソッドの実装を複雑にしすぎないでください
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 21b623041bdf599439fd51f99354f206eb25c433
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893157"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502:メソッドの実装を複雑にしすぎないでください

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|カテゴリ|Microsoft.Maintainability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

メソッドは、サイクロマティック複雑です。

## <a name="rule-description"></a>規則の説明

*サイクロマティック複雑度*線形独立のメソッド、条件付き分岐の複雑さと数によって決定される経路の数を計測します。 低サイクロマティック複雑度には、理解、テスト、および保守しやすい方法通常を示します。 サイクロマティック複雑度を使用して、メソッドの制御フロー グラフから計算されますが、次のように指定します。

サイクロマティック複雑度エッジ - ノード数 + 1 の数を =

表すノードを論理的な分岐ポイントとエッジ ノードの間に行を表します。

ルールは、サイクロマティック複雑度が 25 を超える場合、違反を報告します。

コード メトリックに関する詳細については、[を測定する複雑さとマネージ コードの保守容易性](../code-quality/code-metrics-values.md)、

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するには、サイクロマティック複雑度を減らすための方法をリファクタリングします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告を抑制する場合は、複雑さを軽減することはできません簡単にして、メソッドが理解し、テスト、および保守を容易に安全です。 特に、大規模なを含むメソッド`switch`(`Select`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ステートメントは、候補の除外です。 コード ベースで以前にリリース済みのコードの実行時の動作で予期しない変更を導入したり、開発サイクルの後半は、コードのリファクタリングの保守容易性のメリットを上回る場合がありますが不安定になるリスクです。

## <a name="how-cyclomatic-complexity-is-calculated"></a>サイクロマティック複雑度の計算方法

サイクロマティック複雑度は、次に 1 を加算して計算されます。

- 分岐の数 (など`if`、 `while`、および`do`)

- 数`case`内のステートメント、 `switch`

## <a name="example"></a>例

次の例では、さまざまなサイクロマティック複雑度のあるメソッドを示します。

**1 のサイクロマティック複雑度**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]

## <a name="example"></a>例

**サイクロマティック複雑度 2**

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

## <a name="related-rules"></a>関連するルール

[CA1501:過剰な継承を回避します。](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>関連項目

- [マネージド コードの複雑さと保守性の測定](../code-quality/code-metrics-values.md)