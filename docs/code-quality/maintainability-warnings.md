---
title: 保守性に関する警告
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57bb9e239fdc8272fbf01b45456edcde95503198
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965329"
---
# <a name="maintainability-warnings"></a>保守性に関する警告

保守容易性の警告は、ライブラリとアプリケーションの保守をサポートします。

## <a name="in-this-section"></a>このセクションの内容

| ルール | 説明 |
|-----------|-----------------------------------|
| [CA1500:変数名は、フィールド名と一致する必要があります。](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | インスタンス メソッドでは、パラメーターまたはエラーにつながる、宣言型のインスタンス フィールドと一致する名前を持つローカル変数を宣言します。 |
| [CA1501:過剰な継承を回避します。](../code-quality/ca1501-avoid-excessive-inheritance.md) | 型が、その継承階層内の 5 つ以上深いレベルにあります。 深いレベルで入れ子にされた型の確認、理解、および保守は困難です。 |
| [CA1502:過剰な複雑さを回避します。](../code-quality/ca1502-avoid-excessive-complexity.md) | この規則は、線形独立のメソッド経路数を示す尺度で、条件分岐の数と複雑さによって決まります。 |
| [CA 1504:紛らわしいフィールド名を確認してください。](../code-quality/ca1504-review-misleading-field-names.md) | インスタンス フィールドの名前が「s _」、または静的な名前で始まります (内の共有[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) フィールドが「m _」で開始します。 |
| [CA1505:メンテナンスできないコードを避ける](../code-quality/ca1505-avoid-unmaintainable-code.md) | 型またはメソッドの保守容易性指数が低い値です。 保守容易性指数の低い型またはメソッドは、保守が困難な可能性があるため、デザインの変更を検討することをお勧めします。 |
| [CA1506:過剰なクラスの結合を避ける](../code-quality/ca1506-avoid-excessive-class-coupling.md) | この規則は、型またはメソッドに含まれる一意の型参照の数をカウントすることによって、クラス結合度を計測します。 |

## <a name="see-also"></a>関連項目

- [マネージド コードの複雑さと保守性の測定](../code-quality/code-metrics-values.md)