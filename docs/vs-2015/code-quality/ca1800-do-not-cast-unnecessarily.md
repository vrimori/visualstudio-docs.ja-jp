---
title: 'Ca 1800: 不必要にキャストしません |Microsoft Docs'
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
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7434770acae4c8fba10e40be87413b9dba3a6eaf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260092"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: 不必要にキャストしません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 メソッドは、その引数やローカル変数のいずれかで二重のキャストを実行します。 このルールによって完全に解析、デバッグ情報を使用してテスト対象のアセンブリをビルドする必要があり、関連付けられたプログラム データベース (.pdb) ファイルは、使用可能なである必要があります。

## <a name="rule-description"></a>規則の説明
 二重のキャストがあるとパフォーマンスが低下します。特に、小さな繰り返しステートメントでキャストが実行される場合はそうです。 、明示的な重複するキャスト操作のキャストの結果をローカル変数に格納し、重複するキャスト操作ではなくローカル変数を使用します。

 場合、c#`is`演算子を使用して、実際のキャストを実行すると、前に、キャストが成功するかどうかをテストの結果をテストしてください、`as`演算子代わりにします。 これにより、暗黙のキャスト操作によって実行されることがなく、同じ機能、`is`演算子。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、キャスト操作の数を最小限に抑えるメソッドの実装を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 パフォーマンスが問題ではない場合、この規則による警告を抑制するか、ルールを完全に無視するには安全です。

## <a name="example"></a>例
 次の例は、c# を使用して、規則に違反するメソッドを示しています。`is`演算子。 2 番目のメソッドは、置き換えることで、ルールを満たす、`is`演算子と、テストの結果に対して、`as`演算子で、2 つのイテレーションあたりのキャスト操作の数を減らします。

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>例
 次の例では、メソッド、 `start_Click`、ルール、およびメソッドに違反して複数の重複する明示的なキャストを持つ`reset_Click`キャストをローカル変数に格納することで、規則に適合します。

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>関連項目
 [として](http://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e)[は](http://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)



