---
title: CA1506:クラス結合度を大きくしすぎないでください
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa8d2e85ebacdedfde9d6731ff3e24a557de3e13
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988557"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506:クラス結合度を大きくしすぎないでください

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|カテゴリ|Microsoft.Maintainability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型またはメソッドは、さまざまな種類と結び付いています。

## <a name="rule-description"></a>規則の説明
 この規則は、型またはメソッドに含まれる一意の型参照の数をカウントすることによって、クラス結合度を計測します。

 型およびメソッドを持つクラス結合度の高度な保守が困難なできます。 型と結合度が低く、高い凝集度を示すメソッドを用意することをお勧めします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この違反を修正するには結合されて型の数を減らすには、型またはメソッドを再設計してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 型またはメソッドと見なされます、大量の他の種類への依存関係があるにもかかわらず保守性の高いときに、この警告を除外します。

## <a name="see-also"></a>関連項目

- [保守性の警告](../code-quality/maintainability-warnings.md)
- [マネージド コードの複雑さと保守性の測定](../code-quality/code-metrics-values.md)