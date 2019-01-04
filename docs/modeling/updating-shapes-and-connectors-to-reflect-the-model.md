---
title: シェイプおよびコネクタの更新とモデルへの反映
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 4374f188e0d67e6ce66ad2979b16de959e14d083
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895754"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>シェイプおよびコネクタを更新してモデルに反映する

Visual Studio でのドメイン固有言語では、基になるモデルの状態を反映する図形の外観を行うことができます。

このトピックのコード例に追加する必要があります、`.cs`ファイル、`Dsl`プロジェクト。 各ファイルでこれらのステートメントが必要です。

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>デコレーターの可視性を制御するマップのシェイプのプロパティを設定

DSL 定義で、図形とドメイン クラス間のマッピングを構成することによって、プログラム コードを記述することがなく、デコレーターの可視性を制御できます。 詳細については、次を参照してください。[ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)します。

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>色と形のスタイル プロパティとして公開します。

DSL 定義で、シェイプ クラスを右クリックして**公開されている追加**、項目のいずれかなどのクリックと**塗りつぶしの色**。

図形は、ドメイン プロパティまたはユーザーとしてプログラム コードで設定できるようになりました。 たとえば、コマンドまたはルールのプログラム コードでは、これを設定するに記述できます。

`shape.FillColor = System.Drawing.Color.Red;`

プログラムの制御下でのみ、ユーザーではなく、プロパティの変数を作成する場合など、新しいドメインのプロパティを選択**塗りつぶしの色**DSL 定義図でします。 次に、[プロパティ] ウィンドウで次のように設定します。**参照可能**に`false`設定または**は読み取り専用 UI**に`true`します。

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>色、スタイル、またはモデル要素のプロパティに依存する場所を変更ルールを定義します。
 モデルの他の部分に依存する図形の外観を更新するルールを定義することができます。 たとえば、モデル要素のプロパティに依存するそのシェイプの色を更新するモデル要素のルールの変更を定義できます。 ルールを変更の詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)します。

 元に戻すコマンドを実行すると、規則は呼び出されませんので、ストア内に保持されるプロパティを更新するためだけのルールを使用する必要があります。 これは、図形の可視性とサイズなど、一部のグラフィカル機能には含まれません。 図形のこれらの機能を更新するを参照してください。[非ストア グラフィックの更新機能](#OnAssociatedProperty)します。

 次の例で公開した`FillColor`ドメイン プロパティを前のセクションで説明されているとします。

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

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>OnChildConfigured を使用して、図形のプロパティを初期化するには

図形のプロパティは、最初に設定を作成、上書き`OnChildConfigured()`で図のクラスの部分定義。 図のクラスは、DSL 定義で指定し、生成されたコードが**Dsl\Generated Code\Diagram.cs**します。 例:

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

このメソッドは、ドメインのプロパティと、図形のサイズなど、ストア以外の機能の両方に使用できます。

## <a name="OnAssociatedProperty"></a> AssociateValueWith() を使用して、図形の他の機能を更新するには

図形、影、または、コネクタの矢印のスタイルがかどうかなどの機能の一部のドメインのプロパティとしての機能を公開する組み込みのメソッドはありません。  このような機能に変更は、トランザクション システムの制御下ではありません。 そのため、それらを更新する適切ながないユーザーが元に戻すコマンドを実行するときに、規則が呼び出されないため、規則を使用します。

このような機能を使用して更新する代わりに、<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>します。 次の例では、コネクタの矢印のスタイルは、コネクタを表示するリレーションシップ内のドメイン プロパティの値によって制御されます。

```csharp
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

`AssociateValueWith()` 登録する各ドメイン プロパティに 1 回呼び出すは、必要があります。 指定したプロパティに変更が呼び出しは呼び出された後`OnAssociatedPropertyChanged()`プロパティのモデル要素を表示する任意の図形。

呼び出す必要はありません`AssociateValueWith()`インスタンスごとにします。 InitializeResources はインスタンス メソッドが、各図形クラスに対して 1 回だけ呼び出されます。
