---
title: BoundsRules によってシェイプの位置とサイズが制限される
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 69e189b8348b7c68c7a778f00975d5d1475223ab
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules によってシェイプの位置とサイズが制限される

A*境界ルール*図形の位置とサイズの制限を定義するクラスです。 図形または角また図形のユーザーがドラッグするときに繰り返し呼び出されるメソッドを提供します。

次の例では、固定サイズを水平方向または垂直のバーにするのには、次の四角形を制約します。 ドラッグすると、ユーザー、角また、高さの 2 つの許可されている構成と幅のアウトラインが反転します。

境界のルールがから派生したクラス<xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>です。 ルールのインスタンスは、図形で作成されます。

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
- [対応し、変更を反映](../modeling/responding-to-and-propagating-changes.md)