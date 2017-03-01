---
title: "依存関係図へのカスタム プロパティの追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, adding custom properties
ms.assetid: 52b3ac25-d10b-4507-a1fe-209ccb4d2777
caps.latest.revision: 21
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 6c7e43c180ac5210d9c29961ed7330b370a99075
ms.lasthandoff: 02/22/2017

---
# <a name="add-custom-properties-to-dependency-diagrams"></a>カスタム プロパティの依存関係図を追加します。
依存関係図の拡張コードを記述する場合は、依存関係図の任意の要素と共に値を格納できます。 値は、図が保存され、再び開かれたときに保持されます。 これらのプロパティに表示することもできます、**プロパティ**ウィンドウのユーザーが表示して編集できるようにします。 たとえば、ユーザーが各レイヤーに正規表現を指定できるようにすることや、各レイヤーのクラスの名前がユーザーが指定したパターンに準拠していることを確認するための検証コードをユーザーが記述できるようにすることができます。  
  
## <a name="properties-not-visible-to-the-user"></a>ユーザーに表示されないプロパティ  
 同様に、依存関係図の任意の要素に値をアタッチするコードを作成する場合は、MEF コンポーネントを定義する必要はありません。 という名前のディクショナリがある`Properties` <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement></xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> 。 マーシャリング可能な値を任意のレイヤー要素のディクショナリに単純に追加します。 これらは、依存関係図の一部として保存されます。 詳細については、次を参照してください。[ナビゲートおよび更新プログラムは、プログラム コードでモデルをレイヤー](../modeling/navigate-and-update-layer-models-in-program-code.md)します。  
  
## <a name="properties-that-the-user-can-edit"></a>ユーザーが編集できるプロパティ  
 **最初の準備**  
  
> [!IMPORTANT]
>  プロパティが表示されるようにするには、レイヤーのプロパティが表示されるようにする必要のある各コンピューターで、次の変更を行う必要があります。  
>   
>  1.  メモ帳を使用して、実行**管理者として実行**します。 
          `%ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest` を開きます  
> 2.  
          `Content` 要素内で、次を追加します。  
>   
>     ```xml  
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>  
>     ```  
> 3.  下にある、 **Visual Studio Tools** 、Visual Studio アプリケーション スタート メニューの開いているセクション**開発者コマンド プロンプト**します。  
>   
>      次のように入力します。  
>   
>      `devenv /rootSuffix /updateConfiguration`  
>   
>      `devenv /rootSuffix Exp /updateConfiguration`  
> 4.  Visual Studio を再起動します。  
  
 **コードが VSIX プロジェクトになっていることを確認します。**  
  
 プロパティがコマンド、ジェスチャ、または検証プロジェクトの一部である場合、何も追加する必要はありません。 カスタム プロパティのコードは、MEF コンポーネントとして定義された Visual Studio 機能拡張プロジェクトで定義する必要があります。 詳細については、次を参照してください。[依存関係図にコマンドおよびジェスチャを追加](../modeling/add-commands-and-gestures-to-layer-diagrams.md)または[依存関係ダイアグラムへのカスタム アーキテクチャ検証の追加](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)します。  
  
 **カスタム プロパティを定義します。**  
  
 カスタム プロパティを作成するには、次のようなクラスを定義します。  
  
```  
[Export(typeof(IPropertyExtension))]  
public class MyProperty   
      : PropertyExtension<ILayerElement>  
{  
  // Implement the interface.  
}  
```  
  
 プロパティを定義するには<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>またはその派生クラスを含める:</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>  
  
-   `ILayerModel` - モデル  
  
-   `ILayer` - 各レイヤー  
  
-   `ILayerDependencyLink` - レイヤー間のリンク  
  
-   `ILayerComment`  
  
-   `ILayerCommentLink`  
  
## <a name="example"></a>例  
 次のコードは、標準的なカスタム プロパティ記述子です。 この例では、Boolean プロパティがレイヤー モデル (`ILayerModel`) で定義されており、ユーザーはこれを使用してカスタム検証メソッドに値を提供できます。  
  
```  
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
 [依存関係図を拡張します。](../modeling/extend-layer-diagrams.md)

