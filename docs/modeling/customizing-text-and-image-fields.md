---
title: テキストおよびイメージ フィールドのカスタマイズ
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 01a55cbf2bf8d741594bae273389086e50dcc981
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953132"
---
# <a name="customizing-text-and-image-fields"></a>テキストおよびイメージ フィールドのカスタマイズ
図形のテキスト デコレータを定義するときは、テキスト フィールドで表されます。 テキスト フィールドとその他の ShapeFields の初期化の例については、DSL ソリューションで Dsl\GeneratedCode\Shapes.cs を検査します。

 テキスト フィールドは、ラベルに割り当てられている領域など、図形内の領域を管理するオブジェクトです。 TextField インスタンスを 1 つは、同じクラスの多くの図形の間で共有されます。 TextField インスタンスがインスタンスごとに個別にラベルのテキストを格納しません。 代わりに、、`GetDisplayText(ShapeElement)`メソッドは、パラメーターとして図形を受け取り、図形とそのモデル要素の現在の状態に依存するテキストを検索できます。

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>テキスト フィールドの外観を決定する方法
 `DoPaint()`メソッドが呼び出された表示するフィールド、画面にします。 既定値をオーバーライドすることができますか、`DoPaint(),`またはそれが呼び出すメソッドの一部をオーバーライドすることができます。 次の簡略化されたバージョンの既定のメソッドは、既定の動作をオーバーライドする方法を理解するのに役立ちます。

```
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape's styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application's styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape's styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application's styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }

```

 その他のいくつかのペアがあります。`Get`メソッドおよび`Default`プロパティなど`DefaultMultipleLine/GetMultipleLine()`です。 図形フィールドのすべてのインスタンスの値を変更する既定のプロパティに値を割り当てることができます。 別、または、図形、またはそのモデル要素の状態に依存する 1 つの図形のインスタンスを異なる値を作成するには、上書き、`Get`メソッドです。

## <a name="static-customizations"></a>静的なカスタマイズ
 この図形フィールドのすべてのインスタンスを変更する場合は、最初に、DSL 定義で、プロパティを設定するかどうかを調べてください。 たとえば、[プロパティ] ウィンドウでは、フォント サイズとスタイルを設定できます。

 オーバーライドしていない場合は、`InitializeShapeFields`図形クラス、および割り当てを適切な値のメソッド`Default...`テキスト フィールドのプロパティです。

> [!WARNING]
>  オーバーライドする`InitializeShapeFields()`、設定する必要があります、 **double 型の派生を生成**の図形のクラスのプロパティ`true`DSL 定義します。

 この例では、ユーザー コメントとして使用されるテキスト フィールドが図形にあります。 標準のコメントのフォントを使用することができます。 スタイル セットから標準フォントであるために、既定のフォント id を設定できます。

```

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;

```

## <a name="dynamic-customizations"></a>動的なカスタマイズ
 異なる外観を図形、またはそのモデル要素の状態に依存するためには、独自のサブクラスを派生`TextField`1 つまたは複数のオーバーライドと`Get...`メソッドです。 図形の InitializeShapeFields メソッドをオーバーライドし、独自のクラスのインスタンスで、テキスト フィールドのインスタンスを 必要がありますもします。

 次の例では、テキスト フィールドのフォントが図形のモデル要素のブール型のドメイン プロパティの状態に依存します。

 このコード例を実行するには、最小限の言語のテンプレートを使用して新しい DSL ソリューションを作成します。 ブール型のドメインのプロパティを追加`AlternateState`ExampleElement ドメイン クラスにします。 アイコン デコレータを ExampleShape クラスに追加し、そのイメージをビットマップ ファイルに設定します。 をクリックして**すべてのテンプレートを変換**です。 DSL プロジェクトで、新しいコード ファイルを追加し、次のコードを挿入します。

 コードをテストするには、f5 キーを押して、ソリューションでは、デバッグ、サンプルのダイアグラムを開きます。 アイコンの既定の状態が表示されます。 図形を選択し、[プロパティ] ウィンドウでの値を変更、 **AlternateState**プロパティです。 要素名のフォントを変更する必要があります。

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }

```

## <a name="style-sets"></a>スタイル セット
 上記の例では、使用可能な任意のフォント、テキスト フィールドを変更する方法を示します。 ただし、推奨メソッドは、図形、またはアプリケーションに関連付けられている一連のスタイルのいずれかに変更します。 オーバーライドするには、<xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A>または GetTextBrushId() です。

 または、オーバーライドすることで、図形のスタイル セットの変更を検討<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>です。 これは、フォントおよびすべての図形フィールドのブラシの変更の影響です。

## <a name="customizing-image-fields"></a>イメージ フィールドのカスタマイズ
 図形、画像デコレータを定義するときに、イメージ、図形を定義すると、図形が表示されている領域が、ImageField によって管理されます。 ImageFields とその他の ShapeFields の初期化の例については、DSL ソリューションで Dsl\GeneratedCode\Shapes.cs を検査します。

 ImageField、デコレータに割り当てられている領域など、図形内の領域を管理するオブジェクトです。 ImageField インスタンスを 1 つは、同じ図形クラスの多くの図形の間で共有されます。 ImageField インスタンスは、図形ごとに異なるイメージが格納されません。 代わりに、、`GetDisplayImage(ShapeElement)`メソッドは、パラメーターとして図形を受け取り、イメージ、図形とそのモデル要素の現在の状態に依存して調べることができます。

 変数を画像などの特別な動作をする場合は、ImageField から派生した独自のクラスを作成できます。

#### <a name="to-create-a-subclass-of-imagefield"></a>ImageField のサブクラスを作成するには

1.  設定、 **double 型の派生を生成**DSL 定義に親 shape クラスのプロパティです。

2.  上書き、`InitializeShapeFields`図形クラスのメソッドです。

    -   DSL プロジェクトで、新しいコード ファイルを作成し、図形のクラスの部分クラス定義を記述します。 メソッドの定義をオーバーライドします。

3.  コードを調べ、 `InitializeShapeFields` DSL\GeneratedCode\Shapes.cs にします。

     オーバーライド メソッドで基本メソッドを呼び出すし、独自のイメージ フィールド クラスのインスタンスを作成します。 これを使用で正規の画像フィールドを代わりに、 `shapeFields`  ボックスの一覧です。

## <a name="dynamic-icons"></a>動的アイコン
 この例では、変更アイコンが図形のモデル要素の状態に依存します。

> [!WARNING]
>  この例では、ダイナミック イメージ デコレータを作成する方法を示します。 モデルの変数の状態に応じて 1 つまたは 2 つのイメージの間で切り替える場合は、いくつかのイメージ デコレーターを作成し、図形上の同じ位置に配置し、モデルの特定の値に依存する可視性フィルターを設定する方が簡単変数。 このフィルターを設定するには、DSL 定義でマップのシェイプを選択、DSL 詳細 ウィンドウを開きおよびデコレーター タブをクリックします。

 このコード例を実行するには、最小限の言語のテンプレートを使用して新しい DSL ソリューションを作成します。 ブール型のドメインのプロパティを追加`AlternateState`ExampleElement ドメイン クラスにします。 アイコン デコレータを ExampleShape クラスに追加し、そのイメージをビットマップ ファイルに設定します。 をクリックして**すべてのテンプレートを変換**です。 DSL プロジェクトで、新しいコード ファイルを追加し、次のコードを挿入します。

 コードをテストするには、f5 キーを押して、ソリューションでは、デバッグ、サンプルのダイアグラムを開きます。 アイコンの既定の状態が表示されます。 図形を選択し、[プロパティ] ウィンドウでの値を変更、 **AlternateState**プロパティです。 アイコンは、90 度、その図形を回転し表示する必要があります。

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}

```

## <a name="see-also"></a>関連項目

- [シェイプとコネクタの定義](../modeling/defining-shapes-and-connectors.md)
- [ダイアグラムへの背景イメージの設定](../modeling/setting-a-background-image-on-a-diagram.md)
- [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)