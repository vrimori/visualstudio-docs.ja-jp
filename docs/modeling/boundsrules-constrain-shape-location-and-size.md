---
title: "BoundsRules によってシェイプの位置とサイズが制限される | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメイン固有言語, イベント"
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 18
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 18
---
# BoundsRules によってシェイプの位置とサイズが制限される
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*境界の規則は* 図形のサイズと位置の制限を定義するクラスです。  ユーザーは形状または図形の角は側のドラッグ中に繰り返し呼び出すメソッドを提供します。  
  
 次の例は固定サイズのバーとして図形の四角形を水平または垂直抑制します。  ユーザーが側または角をドラッグするとアウトラインは高さと幅の 2 種類の構成時に使用できる反転させます。  
  
 境界の規則は <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> から派生したクラスです。  規則のインスタンスは図形に作成されます :  
  
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
  
 は位置とサイズを抑制できることに注意してください。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [変更内容への対応および変更内容の反映](../modeling/responding-to-and-propagating-changes.md)