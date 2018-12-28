---
title: CA1505:メンテナンスできないコードを避ける
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7678b0f6b435929c9e53a40062155842e273bbdc
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2018
ms.locfileid: "53740313"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505:メンテナンスできないコードを避ける

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|カテゴリ|Microsoft.Maintainability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 型またはメソッドの保守容易性指数が低い値です。

## <a name="rule-description"></a>規則の説明
 保守容易性指数は、次のメトリックを使用して計算されます。 行のコード、プログラムのボリューム、およびサイクロマティック複雑度。 プログラムのボリュームは、型または演算子とオペランドのコードの数に基づいているメソッドの理解の難しさの尺度です。 サイクロマティック複雑度は、型またはメソッドの構造上の複雑さの基準です。 コード メトリックに関する詳細については、[を測定する複雑さとマネージ コードの保守容易性](../code-quality/code-metrics-values.md)します。

 保守性が低いインデックスことを示します型またはメソッドを維持するが困難な可能性が再設計に適した候補となります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この違反を修正するには、型またはメソッドを再設計し、小さくなりより対象を絞った型またはメソッドに分割することをお試しください。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 型またはメソッドと見なされます、大きなサイズに関係なく、または、型またはメソッドを分割することはできません、保守性の高いときに、この警告を除外します。

## <a name="see-also"></a>関連項目

- [保守性の警告](../code-quality/maintainability-warnings.md)
- [マネージド コードの複雑さと保守性の測定](../code-quality/code-metrics-values.md)