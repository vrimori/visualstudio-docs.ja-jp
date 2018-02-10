---
title: "図形とコネクタ、モデルを反映するように更新 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6d50d0258a44553451deed68a8ccf17c60d88965
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>シェイプおよびコネクタの更新とモデルへの反映
ドメイン固有言語[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、基になるモデルの状態を反映する図形の外観を行うことができます。  
  
 このトピックのコード例に追加する必要があります、`.cs`ファイルで、`Dsl`プロジェクト。 各ファイルにこれらのステートメントを必要となります。  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>デコレーターの可視性を制御する図形マップ プロパティを設定します。  
 DSL 定義で、図形とドメイン クラス間のマッピングを構成することによって、プログラム コードを記述することがなくデコレーターの可視性を制御できます。 詳細については、次を参照してください。[ドメイン固有言語の定義方法](../modeling/how-to-define-a-domain-specific-language.md)です。
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>色と形のスタイル プロパティとして公開します。  
 DSL 定義 shape クラスを右クリックし、**公開追加**、クリックして、項目のいずれかのように**塗りつぶしの色**です。  
  
 図形には、今すぐプログラム コードやユーザーとして設定できるドメイン プロパティがあります。 たとえば、コマンドまたはルールのプログラム コードで設定して、記述することも。  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 プログラムの制御下でのみ、ユーザーではなく、プロパティの変数を作成する場合など、新しいドメインのプロパティを選択**塗りつぶしの色**DSL 定義ダイアグラムにします。 次に、[プロパティ] ウィンドウで次のように設定します。**は参照可能な**に`false`設定または**は UI の読み取り専用**に`true`です。  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>色、スタイル、または場所のモデル要素のプロパティに依存する変更の規則を定義します。  
 モデルの他の部分に依存する図形の外観を更新する規則を定義できます。 たとえば、モデル要素のプロパティに依存するその図形の色を更新するモデル要素に、ルールの変更を定義できます。 ルールを変更の詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)です。  
  
 ルールは、元に戻すコマンドを実行すると、ルールが呼び出されないためには、ストア内で保持されているプロパティを更新のみを使用する必要があります。 これは、図形の可視性とサイズなどのグラフィカルな一部の機能には含まれません。 図形のこれらの機能を更新するを参照してください。[非ストア グラフィックの更新機能](#OnAssociatedProperty)します。  
  
 次の例では公開した`FillColor`ドメイン プロパティの前のセクションで説明されているとします。  
  
```csharp  
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
 図形のプロパティは、最初に設定を作成、上書き`OnChildConfigured()`ダイアグラム クラスの部分定義でします。 図のクラスは、DSL 定義で指定し、生成されたコードは、 **Dsl\Generated Code\Diagram.cs**です。 例:  
  
```csharp  
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
  
##  <a name="OnAssociatedProperty"></a>AssociateValueWith() を使用して、図形の他の機能を更新  
 一部の機能に影をまたは、コネクタの矢印のスタイルなどの図形のドメインのプロパティとして、機能を公開するための組み込みのメソッドはありません。  このような機能に対する変更は、トランザクション システムの制御下ではありません。 したがって、それらを更新する適切ではありません、ユーザーが元に戻すコマンドを実行するときに、規則が呼び出されないため、規則を使用します。  
  
 使用してこのような機能を更新する代わりに、<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>です。 次の例では、コネクタの矢印のスタイルは、コネクタを表示するリレーションシップ内のドメイン プロパティの値によって制御されます。  
  
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
        { // Update the shape's built-in Decorator feature:  
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
  
 `AssociateValueWith()`登録するドメインの各プロパティにつき 1 回として呼び出す必要があります。 指定したプロパティへの変更が呼び出すことが呼び出された後`OnAssociatedPropertyChanged()`プロパティのモデル要素を表示するすべての図形にします。  
  
 呼び出す必要はありません`AssociateValueWith()`インスタンスごとにします。 InitializeResources には、インスタンス メソッドが、各図形クラスに対して 1 回だけ呼び出されます。
