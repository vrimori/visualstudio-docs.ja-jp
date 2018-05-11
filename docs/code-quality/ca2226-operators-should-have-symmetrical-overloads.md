---
title: 'CA2226: 演算子は対称型オーバーロードを含まなければなりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67cdfd3799b0ba3e1af53cb9e95bb426fec02ddf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: 演算子は対称型オーバーロードを含まなければなりません
|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 型で等値演算子または非等値演算子を実装し、逆の働きをする演算子を実装していません。

## <a name="rule-description"></a>規則の説明
 ここで等値または非等値のいずれかは、型のインスタンスに適用され、反対側の演算子が定義されていない状況はありません。 種類は、通常、等値演算子の負数化された値を返すことによって、非等値演算子を実装します。

 C# コンパイラでは、この規則違反のエラーを発行します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、等しいかどうかと、非等値演算子の両方を実装または存在するものを削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 種類と一貫性のある方法で動作しません、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。

## <a name="related-rules"></a>関連規則
 [CA1046: 参照型で、演算子 equals をオーバーロードしないでください](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: 演算子オーバーロードには名前付けされた代替が存在します](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: オーバーライドする Equals で GetHashCode をオーバーライドします](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)