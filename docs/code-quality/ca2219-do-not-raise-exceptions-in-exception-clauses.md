---
title: 'CA2219: exception 句に例外を発生させないでください'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f8b542c88c62230f60b11ba9927873d2593157c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: exception 句に例外を発生させないでください
|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|なし、あり|

## <a name="cause"></a>原因
 例外をスロー、`finally`フィルター、または fault 句。

## <a name="rule-description"></a>規則の説明
 Exception 句で例外が発生した、ときに、デバッグの難易度が大幅に増加します。

 例外が発生すると、`finally`または fault 句では、新しい例外非アクティブな例外が存在する場合。 これにより、元のエラーの検出およびデバッグが困難にします。

 例外が発生すると、フィルター句で、ランタイムはサイレント モードで、例外をキャッチし、フィルターを false に評価されます。 False とフィルターからスローされる例外を評価するフィルターの違いを確認する方法はありません。 検出し、フィルターのロジックでエラーのデバッグが困難になります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則は、この違反を修正するのには明示的に例外を発生させないから、`finally`フィルター、または fault 句。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 Exception 句で発生した例外コードの実行に利点をもたらすシナリオはありません。

## <a name="related-rules"></a>関連規則
 [CA1065: 予期しない場所に例外を発生させません](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>関連項目
 [デザインの警告](../code-quality/design-warnings.md)