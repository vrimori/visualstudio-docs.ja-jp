---
title: CA1023:インデクサーを多次元にすることはできません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a9b708b1be65b8aefa34e9f0366a87d6f94b5b5c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2019
ms.locfileid: "55043701"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023:インデクサーを多次元にすることはできません

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型には、1 つ以上のインデックスを使用するパブリックまたはプロテクトのインデクサーが含まれています。

## <a name="rule-description"></a>規則の説明
 インデクサー、つまり、インデックス付きプロパティには、1 つのインデックスを使用する必要があります。 多次元のインデクサーでは、ライブラリの使いやすさを大幅に短縮できます。 デザインは、複数のインデックスを必要とする場合は、型は、論理データ ストアを表すかどうかを再確認します。 それ以外の場合は、メソッドを使用します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、唯一の整数または文字列のインデックスを使用してデザインを変更またはインデクサーではなく、メソッドを使用します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 非標準のインデクサーの必要性を慎重に検討した後にのみこの規則による警告を抑制します。

## <a name="example"></a>例
 次の例は、型`DayOfWeek03`規則に違反する多次元のインデクサーを使用します。 インデクサーは変換の種類として見なすことができ、そのため、メソッドとして公開がより適切にします。 型がで再設計されました`RedesignedDayOfWeek03`ルールを満たすためにします。

 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>関連するルール
 [CA 1043:インデクサーは整数または文字列引数を使用して、](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA 1024:適切な場所のプロパティを使用します。](../code-quality/ca1024-use-properties-where-appropriate.md)