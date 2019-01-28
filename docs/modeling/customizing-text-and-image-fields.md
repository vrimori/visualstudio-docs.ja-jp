---
title: テキストおよびイメージ フィールドのカスタマイズ
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: bb603a6a99335d17d204fe342cf8d696d8e9021a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919812"
---
# <a name="customizing-text-and-image-fields"></a>テキストおよびイメージ フィールドのカスタマイズ
図形のテキスト デコレータを定義するときに、テキスト フィールドで表されます。 テキスト フィールドとその他の ShapeFields の初期化の例については、DSL ソリューションで Dsl\GeneratedCode\Shapes.cs を検査します。

 テキスト フィールドは、ラベルに割り当てられている領域などの図形内の領域を管理するオブジェクトです。 テキスト フィールドの 1 つのインスタンスは、同じクラスの多くの図形の間で共有されます。 テキスト フィールドのインスタンスはインスタンスごとに個別にラベルのテキストを格納しません。 代わりに、、`GetDisplayText(ShapeElement)`メソッド、図形をパラメーターとして受け取り、図形と、モデル要素の現在の状態に依存するテキストを調べることができます。

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>テキスト フィールドの外観を決定する方法
 `DoPaint()`メソッドが呼び出されたに表示されるフィールド、画面にします。 既定値をオーバーライドすることができますか`DoPaint(),`または呼び出されるメソッドの一部をオーバーライドすることができます。 次の簡略化されたバージョンの既定のメソッドは、既定の動作をオーバーライドする方法を理解するのに役立ちます。

```csharp
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

 他のいくつかのペアがある`Get`メソッドと`Default`プロパティなど`DefaultMultipleLine/GetMultipleLine()`します。 図形フィールドのすべてのインスタンスの値を変更する既定のプロパティに値を割り当てることができます。 もう 1 つ、または、モデル要素または図形の状態に依存する図形の 1 つのインスタンスを異なる値を作成するには、オーバーライド、`Get`メソッド。

## <a name="static-customizations"></a>静的なカスタマイズ
 この図形のフィールドのすべてのインスタンスを変更する場合は、最初に、DSL 定義で、プロパティを設定するかどうかを調べてください。 たとえば、プロパティ ウィンドウで、フォント サイズとスタイルを設定できます。

 そうでない場合、上書き、`InitializeShapeFields`を適切な値を割り当てます、図形のクラスのメソッド`Default...`テキスト フィールドのプロパティ。

> [!WARNING]
>  オーバーライドする`InitializeShapeFields()`を設定する必要があります、 **Double Derived の生成**の図形クラスのプロパティ`true`DSL 定義でします。

 この例では、ユーザーのコメントを使用するテキスト フィールドが図形にあります。 標準のコメントのフォントを使用します。 スタイルのセットから標準フォントであるために、既定のフォント id を設定できます。

```csharp

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
 異なる外観を図形または、モデル要素の状態に依存するためには、派生の独自のサブクラス`TextField`1 つまたは複数のオーバーライドと`Get...`メソッド。 図形の InitializeShapeFields メソッドをオーバーライドし、テキスト フィールドのインスタンスを置き換えて、独自のクラスのインスタンスをする必要がありますもします。

 次の例では、テキスト フィールドのフォントが図形のモデル要素のブール型のドメイン プロパティの状態に依存します。

 この例のコードを実行するには、最小言語テンプレートを使用して、新しい DSL ソリューションを作成します。 ブール型のドメイン プロパティを追加`AlternateState`ExampleElement ドメイン クラスにします。 ExampleShape クラスに、アイコン デコレータを追加し、そのイメージをビットマップ ファイルに設定します。 クリックして**すべてのテンプレートの変換**します。 DSL プロジェクトで新しいコード ファイルを追加し、次のコードを挿入します。

 コードをテストするには、f5 キーを押して、デバッグのソリューションで図のサンプルを開きます。 アイコンの既定の状態が表示されます。 図形を選択し、[プロパティ] ウィンドウでの値を変更、 **AlternateState**プロパティ。 要素名のフォントを変更する必要があります。

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

## <a name="style-sets"></a>スタイルのセット
 前の例では、使用できる任意のフォント、テキスト フィールドを変更する方法を示します。 ただし、図形、またはアプリケーションに関連付けられている一連のスタイルのいずれかに変更することをお勧めメソッドです。 オーバーライドするには、<xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A>または GetTextBrushId() します。

 または、オーバーライドすることで、図形のスタイル セットの変更を検討<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>します。 フォントと図形のフィールドのすべてのブラシの変更の効果があります。

## <a name="customizing-image-fields"></a>イメージ フィールドのカスタマイズ
 図形、イメージのデコレータを定義するときに、およびイメージ シェイプを定義するときに、図形を表示する領域は、ImageField によって管理されます。 ImageFields とその他の ShapeFields の初期化の例については、DSL ソリューションで Dsl\GeneratedCode\Shapes.cs を検査します。

 ImageField、デコレーターに割り当てられている領域などの図形内の領域を管理するオブジェクトです。 ImageField インスタンスを 1 つは、同じ図形クラスの多くの図形の間で共有されます。 ImageField インスタンスは、各図形に別のイメージを格納しません。 代わりに、、`GetDisplayImage(ShapeElement)`メソッド、図形をパラメーターとして受け取り、イメージ、図形と、モデル要素の現在の状態に依存して調べることができます。

 可変の画像などの特別な動作をする場合は、ImageField から派生した独自のクラスを作成できます。

#### <a name="to-create-a-subclass-of-imagefield"></a>ImageField のサブクラスを作成するには

1.  設定、 **Double Derived の生成**DSL 定義で親シェイプ クラスのプロパティ。

2.  上書き、`InitializeShapeFields`図形クラスのメソッド。

    -   DSL プロジェクトで新しいコード ファイルを作成し、シェイプ クラスの部分クラス定義を記述します。 メソッドの定義をオーバーライドします。

3.  コードを調べ、 `InitializeShapeFields` DSL\GeneratedCode\Shapes.cs でします。

     オーバーライド メソッドで基本メソッドを呼び出しておよびイメージ フィールド クラスのインスタンスを作成します。 これで通常の画像フィールドを置換を使用して、`shapeFields`一覧。

## <a name="dynamic-icons"></a>動的アイコン
 この例では、変更アイコンが図形のモデル要素の状態に依存します。

> [!WARNING]
>  この例では、動的な画像デコレーターを作成する方法を示します。 モデルの変数の状態に応じて 1 つまたは 2 つのイメージ間で切り替える場合は、いくつかのイメージのデコレータを作成し、図形の上の同じ位置に配置し、モデルの特定の値に依存する可視性フィルターを設定する方が簡単変数。 このフィルターを設定するに、DSL 定義でマップのシェイプを選択します。 DSL の詳細 ウィンドウを開き、デコレーター タブをクリックします。

 この例のコードを実行するには、最小言語テンプレートを使用して、新しい DSL ソリューションを作成します。 ブール型のドメイン プロパティを追加`AlternateState`ExampleElement ドメイン クラスにします。 ExampleShape クラスに、アイコン デコレータを追加し、そのイメージをビットマップ ファイルに設定します。 クリックして**すべてのテンプレートの変換**します。 DSL プロジェクトで新しいコード ファイルを追加し、次のコードを挿入します。

 コードをテストするには、f5 キーを押して、デバッグのソリューションで図のサンプルを開きます。 アイコンの既定の状態が表示されます。 図形を選択し、[プロパティ] ウィンドウでの値を変更、 **AlternateState**プロパティ。 アイコンは、90 度、その図形を回転し、表示する必要があります。

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