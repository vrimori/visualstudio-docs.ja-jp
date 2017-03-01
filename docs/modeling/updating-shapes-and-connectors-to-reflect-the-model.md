---
title: "図形とコネクタ、モデルを反映するように更新 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 97ec749c0a89dae6c5a98702926d8ad82b6af3ac
ms.lasthandoff: 02/22/2017

---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>シェイプおよびコネクタの更新とモデルへの反映
ドメイン固有言語[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、基になるモデルの状態を反映して、図形の外観を行うことができます。  
  
 このトピックのコード例に追加する必要があります、`.cs`ファイルで、`Dsl`プロジェクトです。 各ファイルにこれらのステートメントを必要となります。  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>デコレーターの可視性を制御する図形マップ プロパティの設定  
 DSL 定義で、図形とドメイン クラス間のマッピングを構成することによって、プログラム コードを記述することがなくデコレーターの可視性を制御できます。 詳細については、次を参照してください。 [ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)します。
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>色と形のスタイル プロパティとして公開します。  
 DSL 定義では、shape クラスを右クリックし、順にポイント**公開されている追加**、クリックして、項目のいずれかなど、**塗りつぶしの色**します。  
  
 図形は、ドメイン プロパティまたはユーザーとしてプログラム コードで設定できるようになりました。 たとえば、コマンドまたはルールのプログラム コードで設定するに記述できます。  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 プログラムの制御下でのみ、ユーザーではなく、プロパティの変数を作成する場合など、新しいドメインのプロパティを選択**塗りつぶしの色**DSL 定義図にします。 次に、[プロパティ] ウィンドウで次のように設定します。**はブラウズ可能な**に`false`設定または**は読み取り専用 UI**に`true`します。  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>色、スタイルまたは場所のモデル要素のプロパティに依存することの変更ルールを定義します。  
 モデルの他の部分に依存して、図形の外観を更新するルールを定義することができます。 たとえば、モデル要素のプロパティに依存して、図形の色を更新するモデル要素には、ルールの変更を定義できます。 ルールを変更の詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)します。  
  
 ルールは、元に戻すコマンドが実行されるときに、規則が呼び出されないためには、ストア内で保持されているプロパティを更新のみを使用する必要があります。 これは、サイズ、形状の表示などのいくつかのグラフィカル機能には含まれません。 図形の機能を更新するを参照してください。[非ストア グラフィックの更新機能](#OnAssociatedProperty)です。  
  
 次の例は、公開したと想定しています。`FillColor`ドメイン プロパティの前のセクションで説明されているとします。  
  
```c#  
[RuleOn(typeof(ExampleElement))]  
  class ExampleElementPropertyRule : ChangeRule  
  {  
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)  
    {  
      base.ElementPropertyChanged(e);  
      ExampleElement element = e.ModelElement as ExampleElement;  
      // The rule is called for every property that is updated.  
      // Therefore, verify which property changed:  
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)  
      {  
        // There is usually only one shape:  
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))  
        {  
          ExampleShape shape = pel as ExampleShape;  
          // Replace this with a useful condition:  
          shape.FillColor = element.Name.EndsWith("3")   
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
        }  
      }  
    }  
  }  
  // The rule must be registered:  
  public partial class OnAssociatedPropertyExptDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(ExampleElementPropertyRule));  
      // If you add more rules, list them here.   
      return types.ToArray();  
    }  
  }  
  
```  
  
## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>図形のプロパティを初期化するために使用する OnChildConfigured  
 図形のプロパティは、最初に設定を作成、上書き`OnChildConfigured()`で図のクラスの部分定義します。 図クラスは、DSL 定義で指定し、生成されたコードは**Dsl\Generated Code\Diagram.cs**します。 例:  
  
```c#  
partial class MyLanguageDiagram  
{  
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)  
  {  
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);  
    ExampleShape shape = child as ExampleShape;  
    if (shape != null)   
    {  
      if (!createdDuringViewFixup) return; // Ignore load from file.  
      ExampleElement element = shape.ModelElement as ExampleElement;  
      // Replace with a useful condition:  
      shape.FillColor = element.Name.EndsWith("3")   
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
    }  
    // else deal with other types of shapes and connectors.  
  }  
}  
  
```  
  
 このメソッドは、ドメインのプロパティと、図形のサイズなどの非ストア機能の両方に使用できます。  
  
##  <a name="a-nameonassociatedpropertya-use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a>AssociateValueWith() を使用して、図形の他の機能の更新  
 一部の機能は、影、または、コネクタの矢印のスタイルなどの図形の機能は、ドメインのプロパティとして公開するための組み込みのメソッドはありません。  このような機能に対する変更は、トランザクション システムの制御下ではありません。 したがって、これらを更新する適切なことはありません、ユーザーが元に戻すコマンドを実行するときに、規則が呼び出されないため、規則を使用します。  
  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>。</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>を使用して、このような機能を更新する代わりに、 次の例では、コネクタの矢印のスタイルは、コネクタを表示するリレーションシップにドメイン プロパティの値によって制御されます。  
  
```  
public partial class ArrowConnector // My connector class.   
{  
   /// <summary>  
    /// Called whenever a registered property changes in the associated model element.  
    /// </summary>  
    /// <param name="e"></param>  
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)  
    {  
      base.OnAssociatedPropertyChanged(e);  
      // Can be called for any property change. Therefore,  
      // Verify that this is the property we're interested in:  
      if ("IsDirected".Equals(e.PropertyName))  
      {  
        if (e.NewValue.Equals(true))  
        { // Update the shape’s built-in Decorator feature:  
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;  
        }  
        else  
        {  
          this.DecoratorTo = null; // No arrowhead.  
        }  
      }  
    }  
    // OnAssociatedPropertyChanged is called only for properties  
    // that have been registered using AssociateValueWith().  
    // InitializeResources is a convenient place to call this.  
    // This method is invoked only once per class, even though  
    // it is an instance method.   
    protected override void InitializeResources(StyleSet classStyleSet)  
    {  
      base.InitializeResources(classStyleSet);  
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);  
      // Add other properties here.  
    }  
}  
  
```  
  
 `AssociateValueWith()`登録する各ドメイン プロパティに&1; 回呼び出すは、必要があります。 呼び出された後、指定したプロパティに対して変更を加えたが呼び出す`OnAssociatedPropertyChanged()`プロパティのモデル要素を表示するすべての図形にします。  
  
 呼び出す必要はありません`AssociateValueWith()`インスタンスごとにします。 InitializeResources はインスタンス メソッドですが、各図形クラスに対して&1; 回だけ呼び出されます。

