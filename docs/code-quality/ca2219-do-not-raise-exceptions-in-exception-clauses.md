---
title: 'CA2219: exception 句に例外を発生させないでください'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 49baf6fe645df35949f47f2796197977d428427e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885968"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: exception 句に例外を発生させないでください

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|なし、あり|

## <a name="cause"></a>原因
 例外がスローされてから、 `finally`、フィルター処理、または fault 句。

## <a name="rule-description"></a>規則の説明
 例外句で例外が発生した、ときにデバッグの難しさが大幅に増加します。

 例外が発生したとき、 `finally` fault 句では、新しい例外の表示と非アクティブな例外が存在する場合またはします。 これにより、元のエラーが検出およびデバッグが困難にします。

 フィルター句で例外が発生した、ときに、ランタイムはサイレント モードで例外をキャッチし、フィルターが false に評価をします。 False に例外がスロー フィルターからフィルター評価の間の違いを見分ける方法はありません。 検出およびフィルターのロジックでエラーのデバッグが困難になります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則は、この違反を修正するのには明示的に例外が発生しないから、 `finally`、フィルター処理、または fault 句。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則の警告を抑制しないでください。 Exception 句で発生した例外コードの実行に利点をもたらすシナリオはありません。

## <a name="related-rules"></a>関連するルール
 [CA1065: 予期しない場所に例外を発生させません](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>関連項目
 [デザインの警告](../code-quality/design-warnings.md)