---
title: 依存関係図へのカスタム プロパティの追加
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 9a3d16fda5b6a4a21ea60aaf2af3d35678e998e4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979479"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>依存関係図へのカスタム プロパティの追加

依存関係図の拡張機能のコードを記述するときは、依存関係図の任意の要素と共に値を格納できます。 値は、図が保存され、再び開かれたときに保持されます。 これらのプロパティに表示することもできます、**プロパティ**ウィンドウ ユーザーが表示して編集できるようにします。 たとえば、ユーザーが各レイヤーに正規表現を指定できるようにすることや、各レイヤーのクラスの名前がユーザーが指定したパターンに準拠していることを確認するための検証コードをユーザーが記述できるようにすることができます。

## <a name="non-visible-properties"></a>非表示のプロパティ

依存関係図の任意の要素に値をアタッチするコードがたい場合は、MEF コンポーネントを定義する必要はありません。 `Properties` には <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> という名前のディクショナリがあります。 マーシャリング可能な値を任意のレイヤー要素のディクショナリに単純に追加します。 これらは、依存関係図の一部として保存されます。 詳細については、次を参照してください。[への移動と更新プログラムは、プログラム コードでモデルをレイヤー](../modeling/navigate-and-update-layer-models-in-program-code.md)します。

## <a name="editable-properties"></a>編集可能なプロパティ

**最初の準備**

> [!IMPORTANT]
> プロパティを表示するには、するには、レイヤーのプロパティを表示する各コンピューターで、次の変更を行います。
>
> 1. メモ帳を使用して実行**管理者として実行**します。 開いている *%ProgramFiles%\Microsoft Visual Studio [バージョン] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*します。
> 2. 内で、**コンテンツ**要素を追加します。
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
> 3. で、 **Visual Studio Tools**開いている Visual Studio アプリケーション スタート メニューのセクション**開発者コマンド プロンプト**します。 次のように入力します。
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Visual Studio を再起動します。

**コードが VSIX プロジェクトで確認します。**

プロパティがコマンド、ジェスチャ、または検証プロジェクトの一部の場合は、何も追加する必要はありません。 カスタム プロパティのコードは、MEF コンポーネントとして定義された Visual Studio 機能拡張プロジェクトで定義する必要があります。 詳細については、次を参照してください。[依存関係図にコマンドおよびジェスチャを追加](../modeling/add-commands-and-gestures-to-layer-diagrams.md)または[依存関係図へのカスタム アーキテクチャ検証の追加](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)します。

**カスタム プロパティを定義します。**

カスタム プロパティを作成するには、次のようなクラスを定義します。

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> のプロパティまたはその任意の派生クラスのプロパティを定義できます。これには、次のものが含まれます。

-   `ILayerModel` - モデル

-   `ILayer` - 各レイヤー

-   `ILayerDependencyLink` - レイヤー間のリンク

-   `ILayerComment`

-   `ILayerCommentLink`

## <a name="example"></a>例

次のコードは、標準的なカスタム プロパティ記述子です。 この例では、Boolean プロパティがレイヤー モデル (`ILayerModel`) で定義されており、ユーザーはこれを使用してカスタム検証メソッドに値を提供できます。

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>関連項目

- [依存関係図の拡張](../modeling/extend-layer-diagrams.md)
