---
title: CA1043:インデクサーには整数または文字列引数を使用します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2f140e8678bfb03bc29a21b05f6f3bfada76e9e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018566"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043:インデクサーには整数または文字列引数を使用します

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型には、他にもインデックスの型を使用するパブリックまたはプロテクトのインデクサーが含まれています。 <xref:System.Int32?displayProperty=fullName>、 <xref:System.Int64?displayProperty=fullName>、 <xref:System.Object?displayProperty=fullName>、または<xref:System.String?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 インデクサー、つまり、インデックス付きプロパティは、インデックスの整数または文字列型を使用する必要があります。 これらの型は、通常データ構造のインデックス作成に使用され、ライブラリのユーザビリティを向上させます。 使用、<xref:System.Object>型がデザイン時に特定の整数または文字列型を指定できない場合に限定する必要があります。 設計では、インデックスの他の種類が必要とする場合は、型は、論理データ ストアを表すかどうかを再確認します。 論理データ ストアを表さない場合は、メソッドを使用します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、integer または string 型では、インデックスを変更またはインデクサーではなく、メソッドを使用します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 非標準のインデクサーの必要性を慎重に検討した後にのみこの規則による警告を抑制します。

## <a name="example"></a>例
 次の例では、インデクサーを使用する、<xref:System.Int32>インデックス。

 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>関連するルール
 [CA 1023:インデクサーを多次元することはできません。](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA 1024:適切な場所のプロパティを使用します。](../code-quality/ca1024-use-properties-where-appropriate.md)