---
title: 移動し、プログラム コードでレイヤー モデルの更新 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 69286377a302fabc900fe4cf9384bb65d094a378
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214936"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>プログラム コードでレイヤー モデル内を移動し、レイヤー モデルを更新する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックでは、プログラム コードを使ってナビゲートおよび更新できるレイヤー モデルの要素と関係について説明します。 ユーザーの観点から見たレイヤー図に関する詳細については、次を参照してください。[レイヤー図: リファレンス](../modeling/layer-diagrams-reference.md)と[レイヤー図: ガイドライン](../modeling/layer-diagrams-guidelines.md)します。  
  
 このトピックで説明される <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> モデルは、より一般的な <xref:Microsoft.VisualStudio.GraphModel> モデルの入門となります。 作成する場合、[メニュー コマンドまたはジェスチャ拡張](../modeling/add-commands-and-gestures-to-layer-diagrams.md)を使用して、`Layer`モデル。 作成する場合、[レイヤー検証拡張機能](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)を使用する方が簡単、`GraphModel`します。  
  
## <a name="transactions"></a>トランザクション  
 モデルを更新する場合、変更を `ILinkedUndoTransaction` で囲むことを検討します。 これにより変更が 1 つのトランザクションにグループ化されます。 いずれかの変更が失敗した場合、トランザクション全体がロールバックされます。 ユーザーが変更を元に戻した場合は、すべての変更がまとめて元に戻されます。  
  
 詳細については、次を参照してください。[トランザクションを使用してモデルの更新をリンク UML](../modeling/link-uml-model-updates-by-using-transactions.md)します。  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>含有  
 ![ILayer および ILayerModel 両方 Ilayer を含めることができます。](../modeling/media/layerapi-containment.png "LayerApi_Containment")  
  
 レイヤー (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) およびレイヤー モデル (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) には、コメントとレイヤーを含めることができます。  
  
 レイヤー (`ILayer`) は、レイヤー モデル (`ILayerModel`) に含めることも、別の `ILayer` に入れ子にすることもできます。  
  
 コメントまたはレイヤーを作成するには、適切なコンテナーで作成メソッドを使用します。  
  
## <a name="dependency-links"></a>依存関係リンク  
 依存関係リンクはオブジェクトによって表されます。 どちらの方向にもナビゲートできます。  
  
 ![ILayerDependencyLink は 2 つの Ilayer を接続します。](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")  
  
 依存関係リンクを作成するには、`source.CreateDependencyLink(target)` を呼び出します。  
  
## <a name="comments"></a>コメント  
 コメントは、レイヤーまたはレイヤー モデルの中に含めることができ、任意のレイヤー要素にリンクすることもできます。  
  
 ![コメントは、任意のレイヤー要素にアタッチすることができます。](../modeling/media/layerapi-comments.png "LayerApi_Comments")  
  
 コメントは任意の数の要素 (ゼロ個も可能) にリンクすることができます。  
  
 レイヤー要素にアタッチしたコメントを取得するには、次のコードを使用します。  
  
```csharp  
ILayerModel model = diagram.GetLayerModel();   
IEnumerable<ILayerComment> comments =   
   model.Comments.Where(comment =>   
      comment.Links.Any(link => link.Target == layerElement));  
  
```  
  
> [!CAUTION]
>  `Comments` の `ILayer` プロパティは、`ILayer` に含まれるコメントを取得します。 そこにリンクされているコメントは取得しません。  
  
 適切なコンテナーで `CreateComment()` を呼び出すことによってコメントを作成します。  
  
 コメントで `CreateLink()` を使用してリンクを作成します。  
  
## <a name="layer-elements"></a>レイヤー要素  
 モデルに含めることのできるタイプの要素はすべてレイヤー要素です。  
  
 ![レイヤー図のコンテンツは ilayerelement ですです。](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>プロパティ  
 各 `ILayerElement` には `Properties` という名前の文字列の辞書があります。 この辞書を使うと、任意の情報をレイヤー要素にアタッチできます。  
  
## <a name="artifact-references"></a>成果物参照  
 成果物参照 (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) は、ファイル、クラス、フォルダーなどのプロジェクト アイテムとレイヤーとの間のリンクを表します。 ユーザーが、ソリューション エクスプローラー、クラス ビュー、またはオブジェクト ブラウザーからレイヤー図にアイテムをドラッグしてレイヤーを作成または追加すると、成果物が作成されます。 成果物参照はいくつでもレイヤーにリンクできます。  
  
 レイヤー エクスプローラーの各行には成果物参照が表示されます。 詳細については、次を参照してください。[コードからレイヤー図を作成する](../modeling/create-layer-diagrams-from-your-code.md)します。  
  
 成果物参照に関係する主な型およびメソッドは次のとおりです。  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>。 カテゴリ プロパティは、参照される成果物の種類 (クラス、実行ファイル、アセンブリなど) を示します。 カテゴリは、対象となる成果物を識別子が特定する方法を決定します。  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> は、<xref:EnvDTE.Project> または <xref:EnvDTE.ProjectItem> から成果物参照を作成します。 これは非同期操作です。 そのため、作成が完了したときに呼び出すコールバックを通常は提供します。  
  
 レイヤー成果物参照は、ユースケース図の成果物と混同してはなりません。  
  
## <a name="shapes-and-diagrams"></a>図形と図  
 レイヤー モデルでは各要素を表すために 2 つのオブジェクトが使用されます。<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> および <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> です。 `IShape` は、図の位置と形のサイズを表します。 レイヤー モデルでは、すべての `ILayerElement` には 1 つの `IShape` があり、レイヤー図のすべての `IShape` には 1 つの `ILayerElement` があります。 `IShape` は UML モデルにも使用されます。 そのため、すべての `IShape` にレイヤー要素があるわけではありません。  
  
 同様に、<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> は 1 つの <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> に表示されます。  
  
 カスタム コマンドまたはジェスチャ ハンドラーのコードでは、`DiagramContext` インポートから現在の図や現在の形の選択を取得できます。  
  
```  
public class ... {  
[Import]  
    public IDiagramContext DiagramContext { get; set; }  
...  
public void ... (...)   
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;  
  ILayerModel model = diagram.GetLayerModel();  
  if (model != null)  
  { foreach (ILayer layer in model.Layers) { ... }}  
  foreach (IShape selected in diagram.SelectedShapes)  
  { ILayerElement element = selected.GetLayerElement();  
    if (element != null) ... }}  
```  
  
 ![各 ILayerElement は IShape で表示されます。](../modeling/media/layerapi-shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> および <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> も UML モデルを表示するのに使用されます。 詳細については、次を参照してください。[図に UML モデルを表示](../modeling/display-a-uml-model-on-diagrams.md)します。  
  
## <a name="see-also"></a>関連項目  
 [レイヤー図にコマンドおよびジェスチャを追加します。](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [レイヤー図へのカスタム アーキテクチャ検証を追加します。](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [レイヤー図へのカスタム プロパティを追加します。](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [レイヤー図: リファレンス](../modeling/layer-diagrams-reference.md)   
 [レイヤー図: ガイドライン](../modeling/layer-diagrams-guidelines.md)   
 [UML モデルと図の拡張](../modeling/extend-uml-models-and-diagrams.md)



