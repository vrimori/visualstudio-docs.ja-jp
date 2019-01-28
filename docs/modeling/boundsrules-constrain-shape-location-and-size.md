---
title: BoundsRules によってシェイプの位置とサイズが制限される
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 8c6ab2a25838935ff0c0b7dcc860fa9196504974
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986225"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules によってシェイプの位置とサイズが制限される

A*境界ルール*は図形の位置とサイズの制限を定義するクラスです。 ユーザーが、図形またはコーナーまたは図形の辺のドラッグ中に繰り返し呼び出されるメソッドを提供します。

次の例では、四角形にすると、水平方向または垂直方向のいずれかの固定のサイズのバーを制約します。 ユーザーがドラッグ角または横、高さの 2 つの許可されている構成と幅のアウトラインが反転します。

境界ルール クラスから派生<xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>します。 ルールのインスタンスは、図形で作成されます。

```csharp
using Microsoft.VisualStudio.Modeling.Diagrams; ...

public partial class BarShape
{
  /// <summary>
  /// Rule invoked when the user is resizing a shape.
  /// </summary>
  public override BoundsRules BoundsRules
  { get { return new BarBoundsRule(); } }
}

/// <summary>
/// Rule invoked when the user is changing a shape's outline.
/// Provides real-time mouse rubber-band feedback, so must work fast.
/// </summary>
public class BarBoundsRule: BoundsRules
{
  public override RectangleD GetCompliantBounds
     (ShapeElement shape, RectangleD proposedBounds)
  {
    double thickness = 0.1;
    if (proposedBounds.Height > proposedBounds.Width)
    {
      // There is a minimum width for a shape; the width
      // will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
            new SizeD(thickness, proposedBounds.Height));
    }
    else
    {
      // There is a minimum height for a shape; the
      // height will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
         new SizeD(proposedBounds.Width, thickness));
} } }
```

場所とサイズ制約でく場合に注意してください。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>
- [変更に対応し、変更を反映する](../modeling/responding-to-and-propagating-changes.md)