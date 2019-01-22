---
title: CA1800:不必要にキャストしません
ms.date: 10/26/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 1ef6e73812a63fdc4cc4392621ab49b279a32d18
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822030"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800:不必要にキャストしません

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
メソッドは、その引数やローカル変数のいずれかで二重のキャストを実行します。

このルールによって完全に解析、デバッグ情報を使用してテスト対象のアセンブリをビルドする必要があり、関連付けられたプログラム データベース (.pdb) ファイルは、使用可能なである必要があります。

## <a name="rule-description"></a>規則の説明
二重のキャストがあるとパフォーマンスが低下します。特に、小さな繰り返しステートメントでキャストが実行される場合はそうです。 、明示的な重複するキャスト操作のキャストの結果をローカル変数に格納し、重複するキャスト操作ではなくローカル変数を使用します。

場合、c#`is`演算子を使用して、実際のキャストを実行すると、前に、キャストが成功するかどうかをテストの結果をテストしてください、`as`演算子代わりにします。 これにより、暗黙のキャスト操作によって実行されることがなく、同じ機能、`is`演算子。 または、C# 7.0 以降では、使用、`is`演算子[パターン マッチング](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is)型変換をチェックし、1 つの手順でその型の変数に式をキャストします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、キャスト操作の数を最小限に抑えるメソッドの実装を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 パフォーマンスが問題ではない場合、この規則による警告を抑制するか、ルールを完全に無視するには安全です。

## <a name="examples"></a>使用例
 次の例は、c# を使用して、規則に違反するメソッドを示しています。`is`演算子。 2 番目のメソッドは、置き換えることで、ルールを満たす、`is`演算子と、テストの結果に対して、`as`演算子で、2 つのイテレーションあたりのキャスト操作の数を減らします。 3 番目のメソッドを使用しても、ルールを満たす`is`で[パターン マッチング](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is)型変換が成功した場合に必要な型の変数を作成します。

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 次の例では、メソッド、 `start_Click`、ルール、およびメソッドに違反して複数の重複する明示的なキャストを持つ`reset_Click`キャストをローカル変数に格納することで、規則に適合します。

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>関連項目

- [as (C# リファレンス)](/dotnet/csharp/language-reference/keywords/as)
- [is (C# リファレンス)](/dotnet/csharp/language-reference/keywords/is)
