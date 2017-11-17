---
title: "BoundsRules 図形の位置とサイズを制限する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: "18"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 8a611bd18cb06b712f671d370bfc26d4dc8cf4f3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules によってシェイプの位置とサイズが制限される
A*境界ルール*図形の位置とサイズの制限を定義するクラスです。 図形または角また図形のユーザーがドラッグするときに繰り返し呼び出されるメソッドを提供します。  
  
 次の例では、固定サイズを水平方向または垂直のバーにするのには、次の四角形を制約します。 ドラッグすると、ユーザー、角また、高さの 2 つの許可されている構成と幅のアウトラインが反転します。  
  
 境界のルールがから派生したクラス<xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>です。 ルールのインスタンスは、図形で作成されます。  
  
```  
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
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [変更内容への対応および変更内容の反映](../modeling/responding-to-and-propagating-changes.md)