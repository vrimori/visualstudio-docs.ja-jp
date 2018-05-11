---
title: 'CA1023: インデクサーを多次元にすることはできません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3864cbef5a5ba6c013d05112af46d641aa3c1634
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: インデクサーを多次元にすることはできません
|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型には、1 つ以上のインデックスを使用して、パブリックまたはプロテクトのインデクサーが含まれています。

## <a name="rule-description"></a>規則の説明
 インデクサー、つまり、インデックス付きプロパティには、1 つのインデックスを使用する必要があります。 多次元のインデクサーでは、ライブラリの操作性を大幅に削減できます。 設計には、複数のインデックスが必要とする場合は、型の論理データ ストアを表しているかどうかを再確認します。 それ以外の場合は、メソッドを使用します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、整数型または文字列型のインデックスを使用してデザインを変更またはインデクサーではなく、メソッドを使用します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 非標準のインデクサーの必要性を慎重に検討した後にのみこの規則による警告は抑制されます。

## <a name="example"></a>例
 次の例は、型`DayOfWeek03`規則に違反する多次元のインデクサーとします。 インデクサーは、変換の種類として見なすことができ、そのため、メソッドとして公開されるより適切です。 型がで再設計されました`RedesignedDayOfWeek03`ルールを満たすためにします。

 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA1043: インデクサーには整数または文字列引数を使用します](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: 適切な場所にプロパティを使用します](../code-quality/ca1024-use-properties-where-appropriate.md)