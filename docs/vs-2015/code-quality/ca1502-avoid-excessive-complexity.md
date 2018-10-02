---
title: 'CA1502: 過剰な複雑さを回避 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0200d02b0e96e1d09ceb83678e89312bc9fc2e3f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589233"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: メソッドの実装を複雑にしすぎないでください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1502: 過剰な複雑さを回避](https://docs.microsoft.com/visualstudio/code-quality/ca1502-avoid-excessive-complexity)します。

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

 コード メトリックに関する詳細については、[を測定する複雑さとマネージ コードの保守容易性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)、

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、サイクロマティック複雑度を減らすための方法をリファクタリングします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制する場合は、複雑さを軽減することはできません簡単にして、メソッドが理解し、テスト、および保守を容易に安全です。 特に、大規模なを含むメソッド`switch`(`Select`で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) ステートメントは、候補の除外です。 コード ベースで以前にリリース済みのコードの実行時の動作で予期しない変更を導入したり、開発サイクルの後半は、コードのリファクタリングの保守容易性のメリットを上回る場合がありますが不安定になるリスクです。

## <a name="how-cyclomatic-complexity-is-calculated"></a>サイクロマティック複雑度の計算方法
 サイクロマティック複雑度は、次に 1 を加算して計算されます。

-   分岐の数 (など`if`、 `while`、および`do`)

-   数`case`内のステートメント、 `switch`

 次の例では、さまざまなサイクロマティック複雑度のあるメソッドを示します。

## <a name="example"></a>例
 **1 のサイクロマティック複雑度**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#1)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#1)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#1)]

## <a name="example"></a>例
 **サイクロマティック複雑度 2**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#2)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#2)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#2)]

## <a name="example"></a>例
 **3 のサイクロマティック複雑度**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#3)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#3)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#3)]

## <a name="example"></a>例
 **8 のサイクロマティック複雑度**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#4)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#4)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#4)]

## <a name="related-rules"></a>関連規則
 [CA1501: 継承を使用しすぎないでください](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>関連項目
 [マネージド コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



