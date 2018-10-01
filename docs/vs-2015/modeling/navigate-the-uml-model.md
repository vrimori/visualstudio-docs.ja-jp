---
title: UML モデル内を移動 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6c5190e1ec273ac0e0b20855c1d0764b58dda65b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538225"
---
# <a name="navigate-the-uml-model"></a>UML モデル内を移動する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[UML モデル内を移動](https://docs.microsoft.com/visualstudio/modeling/navigate-the-uml-model)します。  
  
ここでは、主要な UML モデルの種類について説明します。  
  
## <a name="the-model-elements-model-and-model-store"></a>モデル要素、モデル、およびモデル ストア  
 アセンブリで定義された型**Microsoft.VisualStudio.Uml.Interfaces.dll**で定義されている型に対応する、 [UML 仕様バージョン 2.1.2](http://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/)します。  
  
 UML 仕様の型は、Visual Studio においてインターフェイスとして実現されます。 それぞれの型の前には、"I" という文字が付加されています。 たとえば、<xref:Microsoft.VisualStudio.Uml.Classes.IElement>、<xref:Microsoft.VisualStudio.Uml.Classes.IClass>、<xref:Microsoft.VisualStudio.Uml.Interactions.IInteraction>、<xref:Microsoft.VisualStudio.Uml.Classes.IOperation> のようになります。  
  
 IElement 以外のすべての型は、1 つ以上のスーパータイプのプロパティを継承します。  
  
-   モデルの種類の概要については、次を参照してください。 [UML モデル要素の型](../modeling/uml-model-element-types.md)します。  
  
-   API の詳細については、次を参照してください。 [UML モデリング機能拡張の API リファレンス](../modeling/api-reference-for-uml-modeling-extensibility.md)します。  
  
### <a name="relationships"></a>リレーションシップ  
 UML 仕様に定義されているプロパティおよび関係は、.NET プロパティとして実装されます。  
  
 ほとんどの関係では、両方向への移動が可能です。 関係はプロパティのペアであり、各端の型の 1 つのプロパティどうしを結び付けるものです。 たとえば、プロパティ `IElement.Owner` および `IElement.OwnedElements` が関係の両端を表します。 したがって、次の式は常に true と評価されます。  
  
 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`  
  
 IAssociation など、多くの関係は、固有のプロパティを指定できるオブジェクトによっても表されます。  
  
 モデルの要素を削除すると、その要素が参加する関係が自動的に削除され、もう一方の端のプロパティが更新されます。  
  
 UML 仕様で 0..1 の多重度がプロパティに割り当てられている場合、その値は `null` になることがあります。 1 は、.NET プロパティが、型を持つことを意味するよりも大きい最大多重度: `IEnumerable<`*型*`>`します。  
  
 関係の走査の詳細については、次を参照してください。 [UML API を使用したリレーションシップをナビゲート](../modeling/navigate-relationships-with-the-uml-api.md)します。  
  
### <a name="the-ownership-tree"></a>所有権ツリー  
 モデルには <xref:Microsoft.VisualStudio.Uml.Classes.IElement> オブジェクトのツリーがあります。 どの要素にもプロパティ `OwnedElements` および `Owner` があります。  
  
 ほとんどの場合、`Owner` プロパティおよび `OwnedElements` プロパティの対象は、より具体的な名前を持つ他のプロパティでも参照されます。 たとえば、UML 操作は、いずれも UML クラスによって所有されます。 したがって、<xref:Microsoft.VisualStudio.Uml.Classes.IOperation> には <xref:Microsoft.VisualStudio.Uml.Classes.IOperation.Class%2A> というプロパティがあり、いずれの <xref:Microsoft.VisualStudio.Uml.Classes.IOperation> オブジェクトでも `Class == Owner` です。  
  
 ツリーの最上位要素 (Owner がない) は <xref:Microsoft.VisualStudio.Uml.AuxiliaryConstructs.IModel> です。 IModel は <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore> に含まれ、そこでは <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore.Root%2A> になります。  
  
 すべてのモデル要素には、作成時に Owner を指定します。 詳細については、次を参照してください。[で UML モデル要素および関係を作成する](../modeling/create-elements-and-relationships-in-uml-models.md)します。  
  
 ![クラス ダイアグラム: モデル、図、図形、および要素](../modeling/media/uml-mm1.png "UML_MM1")  
  
## <a name="shapes-and-diagrams"></a>図形と図  
 UML モデル内の要素を図で表示することができます。 IElement のサブタイプをそれぞれ異なる種類の図に表示できます。  
  
 場合によっては、1 つの要素を複数の図に表示できます。 たとえば、IUseCase 要素には複数の IShapes を追加でき、それらの IShapes を 1 つの図または複数の種類の図に表示できます。  
  
 図形はツリー内に位置付けられます。 ツリーの各端は、ParentShape プロパティと ChildShapes プロパティで表されます。 図は、親のない唯一の図形です。 図のサーフェイス上の図形は、より小さなパートで構成されます。 たとえば、クラスの図形には、属性と操作のコンパートメントがあります。  
  
 図形の詳細については、次を参照してください。[図に UML モデルを表示](../modeling/display-a-uml-model-on-diagrams.md)します。  
  
## <a name="access-to-the-model-in-extensions"></a>拡張機能でのモデルへのアクセス  
 MEF コンポーネントとして定義される [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 拡張機能では、拡張機能が実行されるコンテキストから情報をインポートするプロパティを宣言できます。  
  
|属性の型|アクセスを提供する対象|詳細情報|  
|--------------------|----------------------------------|----------------------|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation<br /><br /> .IDiagramContext<br /><br /> (Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll 内)|現在のフォーカス図。|[モデリング図にメニュー コマンドを定義する](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|  
|Microsoft.VisualStudio.Modeling.ExtensionEnablement<br /><br /> .ILinkedUndoContext<br /><br /> (Microsoft.VisualStudio.Modeling.Sdk.[バージョン].dll 内)|一連の変更をトランザクションにグループ化できます。|[トランザクションを使用して UML モデルの更新をリンクする](../modeling/link-uml-model-updates-by-using-transactions.md)|  
|Microsoft.VisualStudio.Shell .SVsServiceProvider<br /><br /> (Microsoft.VisualStudio.Shell.Immutable.[バージョン].dll 内)|ホスト [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 ここから、ファイル、プロジェクト、および他の側面にアクセスできます。|[Visual Studio API を使用して UML モデルを開く](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)|  
  
### <a name="to-get-the-context"></a>コンテキストを取得するには  
 次に示すインターフェイスのいずれか一方または両方を拡張機能クラス内で宣言します。  
  
```  
[Import] public IDiagramContext DiagramContext { get; set; }  
  
```  
  
 MEF (Managed Extensibility Framework) によりこれらのインターフェイスが定義にバインドされ、これから現在の図、モデル ストア、ルート オブジェクトなどを取得できるようになります。  
  
```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
IClassDiagram classDiagram = diagram as IClassDiagram;  
       // or diagrams of other types  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IDiagram diagram in modelStore.Diagrams) {...}  
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}  
```  
  
### <a name="to-get-the-current-selection"></a>現在の選択項目を取得するには  
  
```  
// All selected shapes and their elements  
foreach (IShape shape in diagram.SelectedShapes)  
{    
   IDiagram selectedDiagram = shape as IDiagram;  
   if (selectedDiagram != null)  
   { // no shape selected - user right-clicked the diagram  
     ... Context.CurrentDiagram ...  
   }  
   else  
   {  
     IElement selectedElement = shape.Element;  
   ...}  
// All selected shapes that display a specfic type of element  
foreach (IShape<IInterface> in   
   diagram.GetSelectedShapes<IInterface>())   
{...}  
```  
  
## <a name="accessing-another-model-or-diagrams"></a>別のモデルまたは図へのアクセス  
 次の操作を行うことができます。  
  
-   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Modelbus を使用し、さまざまなモデルの要素間のリンクを生成します。 詳細については、次を参照してください。[を他のモデルおよびツールとの統合の UML モデル](../modeling/integrate-uml-models-with-other-models-and-tools.md)します。  
  
-   モデリング プロジェクトと図を [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ユーザー インターフェイスに表示させず、読み取り専用で読み込みます。 詳細については、次を参照してください。[プログラム コードで UML モデルを読み取る](../modeling/read-a-uml-model-in-program-code.md)します。  
  
-   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] でモデリング プロジェクトと図を開き、コンテンツにアクセスします。 詳細については、次を参照してください。 [Visual Studio API を使用して UML モデルを開く](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)します。  
  
## <a name="see-also"></a>関連項目  
 [UML モデルと図を拡張します。](../modeling/extend-uml-models-and-diagrams.md)   
 [UML API を使用したプログラミング](../modeling/programming-with-the-uml-api.md)



