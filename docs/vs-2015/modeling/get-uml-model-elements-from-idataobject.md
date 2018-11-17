---
title: IDataObject から UML モデル要素を取得 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a560ce5116c52b8c2e83ce9b28252f060e2485f1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782077"
---
# <a name="get-uml-model-elements-from-idataobject"></a>IDataObject から UML モデル要素を取得する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ユーザーが任意のソースから要素を UML 図にドラッグすると、ドラッグされた要素は `System.Windows.Forms.IDataObject` でエンコードされます。 エンコーディングは、ソース オブジェクトの種類によって決まります。 次のフラグメントでは、ソースが UML 図である場合に要素をどのように取得するかについて示します。  
  
> [!NOTE]
>  UML モデルに対して実行する必要がある操作のほとんどは、型を使用して実行できるは、アセンブリで定義されている**Microsoft.VisualStudio.Uml.Interfaces**と**Microsoft.VisualStudio.ArchitectureTools.Extensibility**します。 しかし、そのためには、UML モデリング ツールの実装の一部であるいくつかのクラスを使用する必要があります。 たとえば、このフラグメントの `ShapeElement` は UML の `IShape` と同じではありません。 UML モデルと図が不整合な状態になる可能性を低くするには、他に方法がない場合を除き、これらの実装クラスに対してメソッドを使用しないことをお勧めします。  
  
## <a name="code-sample"></a>コード サンプル  
 プロジェクトは、次を参照する必要があります[!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]アセンブリ。  
  
 **Microsoft.VisualStudio.Modeling.Sdk します。[バージョン]**  
  
 **Microsoft.VisualStudio.Modeling.Sdk.Diagrams します。[バージョン]**  
  
 **次のコード**  
  
```  
using Microsoft.VisualStudio.Modeling;    
  // for ElementGroupPrototype  
using Microsoft.VisualStudio.Modeling.Diagrams;    
  // for ShapeElement, DiagramDragEventArgs, DiagramPointEventArgs  
…   
  /// <summary>  
  /// Retrieves UML IElements from drag arguments.  
  /// Works for drags from UML diagrams.  
  /// </summary>  
  private IEnumerable<IElement> GetModelElementsFromDragEvent  
                  (DiagramDragEventArgs dragEvent)  
  {  
     //ElementGroupPrototype is the container for  
     //dragged and copied elements and toolbox items.  
     ElementGroupPrototype prototype =  
        dragEvent.Data.  
        GetData(typeof(ElementGroupPrototype))  
                     as ElementGroupPrototype;  
     // Locate the originals in the implementation store.  
     IElementDirectory implementationDirectory =   
        dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;  
  
     return  prototype.ProtoElements.Select(  
       prototypeElement =>   
       {  
          ModelElement element = implementationDirectory  
                .FindElement(prototypeElement.ElementId);  
          ShapeElement shapeElement = element as ShapeElement;  
          if (shapeElement != null)  
          {   
            // Dragged from a diagram.  
            return shapeElement.ModelElement as IElement;  
          }  
          else  
          {   
            // Dragged from UML Model Explorer.  
            return element as IElement;  
          }  
        });  
    }  
```  
  
 詳細については`ElementGroupPrototype`と`Store`、UML モデリング ツールが実装されているを参照してください。 [Modeling SDK for Visual Studio - ドメイン固有言語](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)します。  
  
## <a name="see-also"></a>関連項目  
 [UML API を使用したプログラミング](../modeling/programming-with-the-uml-api.md)   
 [モデリング図にメニュー コマンドを定義する](../modeling/define-a-menu-command-on-a-modeling-diagram.md)



