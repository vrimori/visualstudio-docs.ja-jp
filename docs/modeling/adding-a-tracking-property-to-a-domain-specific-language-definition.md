---
title: ドメイン固有言語の定義への追跡プロパティの追加
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: aec41a7ad2c93d9ad5762f8e4c7e67ea93704f1f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>ドメイン固有言語の定義に追跡プロパティを追加します。

このチュートリアルでは、ドメイン モデルに追跡プロパティを追加する方法を示します。

A*ドメインを追跡*プロパティは、ユーザーが更新できるが、その他のドメインのプロパティまたは要素の値を使用して計算される、既定値を持つプロパティです。

たとえば、ドメイン固有言語ツール (DSL ツール) のドメイン クラスは、ユーザーの名前を使用して計算される既定値を持つドメイン クラスのプロパティ表示名デザイン時に値を変更したり計算値にリセットできます。

このチュートリアルでは、追跡、モデルの既定の Namespace プロパティに基づいて既定値を持つプロパティの Namespace を持つドメイン固有言語 (DSL) を作成します。 プロパティの追跡の詳細については、次を参照してください。[追跡プロパティを定義する](http://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be)です。

-   DSL ツールは、プロパティ記述子の追跡をサポートします。 ただし、DSL デザイナーは、追跡プロパティ、言語を追加するのには使用できません。 そのため、定義および追跡プロパティを実装するカスタム コードを追加する必要があります。

 追跡プロパティが 2 つの状態: 追跡、およびユーザーによって更新されました。 追跡のプロパティでは、次の特徴があります。

-   追跡状態のときに追跡プロパティの値が計算され、モデルの変更時にその他のプロパティとして値が更新されます。

-   更新されたときに、ユーザー状態を追跡プロパティの値には、ユーザー最後設定されるプロパティ値が保持されます。

-   **プロパティ**ウィンドウで、**リセット**コマンド プロパティは、更新されたときにのみ追跡プロパティが有効なユーザーの状態でします。 **リセット**コマンド追跡プロパティ設定を追跡する状態。

-   **プロパティ**ウィンドウ、追跡プロパティが追跡の状態、その値が通常フォントで表示されます。

-   **プロパティ**ウィンドウで、追跡プロパティが更新されたとき、ユーザー状態では、その値が太字のフォントで表示されます。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを開始する前に、これらのコンポーネントをまずインストールする必要があります。

|||
|-|-|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|
|[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|

## <a name="create-the-project"></a>プロジェクトの作成

1.  ドメイン固有言語デザイナー プロジェクトを作成します。 これに `TrackingPropertyDSL` という名前を付けます。

2.  **ドメイン固有言語デザイナー ウィザード**、次のオプションを設定します。

    1.  選択、 **MinimalLanguage**テンプレート。

    2.  ドメイン固有言語の既定の名前を使用して`TrackingPropertyDSL`です。

    3.  モデル ファイルの拡張機能設定`trackingPropertyDsl`です。

    4.  モデル ファイルの既定のテンプレートのアイコンを使用します。

    5.  製品の名前を設定`Product Name`です。

    6.  会社の名前を設定`Company Name`です。

    7.  既定値を使用して、ソリューション内のプロジェクトのルート名前空間の`CompanyName.ProductName.TrackingPropertyDSL`します。

    8.  アセンブリの厳密な名前キー ファイルを作成するウィザードを許可します。

    9. ソリューションの詳細を確認し、をクリックして**完了**DSL 定義プロジェクトを作成します。

## <a name="customize-the-default-dsl-definition"></a>DSL の Default 定義をカスタマイズします。
 このセクションで、次の項目を含む DSL 定義をカスタマイズします。

-   モデルのすべての要素のプロパティを追跡 Namespace です。

-   モデルの各要素に対してブール IsNamespaceTracking プロパティです。 このプロパティは追跡プロパティが追跡状態または更新されたかどうかを指定してユーザー状態です。

-   モデルの既定の Namespace プロパティです。 このプロパティは追跡プロパティ Namespace の既定値の計算に適用されます。

-   モデルの計算 CustomElements プロパティです。 このプロパティは、カスタム名前空間を持つ要素の割合で示されます。

### <a name="to-add-the-domain-properties"></a>ドメインのプロパティを追加するには

1.  DSL デザイナー内を右クリックし、 **ExampleModel**ドメイン クラス、順にポイント**追加**、クリックして**DomainProperty**です。

    1.  新しいプロパティの名前を付けます`DefaultNamespace`です。

    2.  **プロパティ**ウィンドウで、新しいプロパティの設定**既定値**に`DefaultNamespace`、設定と**型**に**文字列**です。

2.  **ExampleModel**ドメイン クラス、という名前のドメインのプロパティを追加`CustomElements`です。

     **プロパティ**ウィンドウで、新しいプロパティの設定**種類**に**Calculated**です。

3.  **ExampleElement**ドメイン クラス、という名前のドメインのプロパティを追加`Namespace`です。

     **プロパティ**ウィンドウで、新しいプロパティの設定**は参照可能な**に**False**、設定と**種類**に**CustomStorage**.

4.  **ExampleElement**ドメイン クラス、という名前のドメインのプロパティを追加`IsNamespaceTracking`です。

     **プロパティ**ウィンドウで、新しいプロパティの設定**は参照可能な**に**False**設定、**既定値**に`true`、し、設定**型**に**ブール**です。

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>図の要素と DSL 詳細を更新するには

1.  DSL デザイナー内を右クリックし、 **ExampleShape** geometry 図形、順にポイント**追加**、クリックして**テキスト デコレータ**です。

    1.  名前を新しいテキスト デコレータ`NamespaceDecorator`です。

    2.  **プロパティ** ウィンドウのテキスト デコレータ設定**位置**に**InnerBottomLeft**です。

2.  DSL デザイナーで選択を結ぶ線、 **ExampleElement**クラスを**ExampleShape**図形です。

    1.  **DSL 詳細**ウィンドウで、**デコレータ マップ**タブです。

    2.  **デコレーター**一覧で、 **NamespaceDecorator**、そのチェック ボックスをオンにし、**プロパティの表示**一覧で、 **Namespace**.

3.  **DSL のエクスプ ローラー**、展開、**ドメイン クラス**フォルダーを右クリックし、 **ExampleElement**ノードをクリックして**新しいドメインの型記述子の追加**.

    1.  展開して、 **ExampleElement**ノード、および選択、**カスタム型記述子 (ドメインの型記述子)** ノード。

    2.  **プロパティ**ウィンドウで、ドメインの型記述子の設定**カスタム コード化された**に**True**です。

4.  **DSL のエクスプ ローラー**、select、 **Xml シリアル化の動作**ノード。

    1.  **プロパティ**ウィンドウで、設定**カスタム Post ロード**に**True**です。

## <a name="transform-templates"></a>テンプレートを変換します。

これで、DSL のドメイン クラスとプロパティを定義することができますを確認することをプロジェクトのコードを再生成する DSL 定義を正しく変換することができます。

1.  **ソリューション エクスプ ローラー**ツールバーで、をクリックして**すべてのテンプレートの変換**です。

2.  システムは、ソリューションのコードを再生成し、DslDefinition.dsl を保存します。 定義ファイルの XML 形式については、次を参照してください。 [DslDefinition.dsl ファイル](../modeling/the-dsldefinition-dsl-file.md)です。

## <a name="create-files-for-custom-code"></a>カスタム コードのファイルを作成します。

すべてのテンプレートを変換すると、システムは、Dsl および DslPackage プロジェクトで、ドメイン固有言語を定義するソース コードを生成します。 生成されたテキストに干渉することを回避することができるように、生成されたコード ファイルから個別のファイルで、カスタム コードを記述します。

値と、追跡プロパティの状態を維持するため、コードを記述する必要があります。 生成されたコードをカスタム コードを区別するために、ファイル名前付けの競合を回避するのには、サブフォルダーに個別に、カスタム コード ファイルを配置します。

1.  **ソリューション エクスプ ローラー**を右クリックし、 **DSL**プロジェクトをポイントし、**追加**、クリックして**新しいフォルダー**です。 新しいフォルダーの名前を付けます`CustomCode`です。

2.  新しいを右クリックし**CustomCode**フォルダーを指す**追加**、順にクリック**新しい項目の**です。

3.  選択、**コード ファイル**テンプレートの設定、**名前**に`NamespaceTrackingProperty.cs`、順にクリック **[ok]** です。

     NamespaceTrackingProperty.cs ファイルが作成され、編集用に開きます。

4.  フォルダーで、次のコード ファイルを作成します: `ExampleModel.cs,``HelperClasses.cs`、 `Serialization.cs`、および`TypeDescriptor.cs`です。

5.  **DslPackage**プロジェクト、作成も、`CustomCode`フォルダーを追加して、`Package.cs`コード ファイル。

## <a name="add-helper-classes-to-support-tracking-properties"></a>プロパティの追跡をサポートするヘルパー クラスを追加します。

HelperClasses.cs ファイルに追加、`TrackingHelper`と`CriticalException`クラスの次のようにします。 このチュートリアルの後半でこれらのクラスを参照します。

1.  HelperClasses.cs ファイルに次のコードを追加します。

    ```csharp
    using System;
    using System.Collections;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        internal static class TrackingHelper
        {
            /// <summary>Notify each model element in a collection that a tracked
            /// property has changed.</summary>
            /// <param name="store">The store for the model.</param>
            /// <param name="collection">The collection of model elements that
            /// contain the tracking property.</param>
            /// <param name="propertyId">The ID of the tracking property.</param>
            /// <param name="trackingPropertyId">The ID of the property that
            /// indicates whether the tracking property is tracking.</param>
            internal static void UpdateTrackingCollectionProperty(
                Store store,
                IEnumerable collection,
                Guid propertyId,
                Guid trackingPropertyId)
            {
                DomainPropertyInfo propInfo =
                    store.DomainDataDirectory.GetDomainProperty(propertyId);

                DomainPropertyInfo trackingPropInfo =
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);

                Debug.Assert(propInfo != null);
                Debug.Assert(trackingPropInfo != null);
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),
                    "Tracking property not specified as a boolean");

                foreach (ModelElement element in collection)
                {
                    // If the tracking property is currently tracking, then notify
                    // it that the tracked property has changed.
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);
                    if (isTracking)
                    {
                        propInfo.NotifyValueChange(element);
                    }
                }
            }
        }

        /// <summary>Helper class to flag critical exceptions from ones that are
        /// safe to ignore.</summary>
        internal static class CriticalException
        {
            /// <summary>Gets whether an exception is critical and can not be
            /// ignored.</summary>
            /// <param name="ex">The exception to check.</param>
            /// <returns>True if the exception is critical.</returns>
            internal static bool IsCriticalException(Exception ex)
            {
                if (ex is NullReferenceException
                    || ex is StackOverflowException
                    || ex is OutOfMemoryException
                    || ex is System.Threading.ThreadAbortException)
                    return true;

                if (ex.InnerException != null)
                    return IsCriticalException(ex.InnerException);

                return false;
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>カスタム型記述子のカスタム コードを追加します。

実装、`GetCustomProperties`メソッドの型記述子を`ExampleModel`ドメイン クラスです。

> [!NOTE]
> カスタム型記述子の DSL ツールを生成するコード`ExampleModel`呼び出し`GetCustomProperties`。 ただし、DSL ツールは、メソッドを実装するコードを生成できません。

このメソッドを定義する、追跡と作成のプロパティを追跡 Namespace プロパティ記述子。 さらに、追跡プロパティの属性を提供することによって、**プロパティ**プロパティを正しく表示するウィンドウです。

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>ExampleModel ドメイン クラスの型記述子を変更するには

1.  TypeDescriptor.cs ファイルに次のコードを追加します。

    ```csharp
    using System;
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the custom type descriptor for the ExampleElement domain class, add
        // the GetCustomProperties method.
        public partial class ExampleElementTypeDescriptor
        {
            /// <summary>Returns the property descriptors for the described
            /// ExampleElement domain class.</summary>
            /// <remarks>This method adds the tracking property descriptor.
            /// </remarks>
            private PropertyDescriptorCollection GetCustomProperties(
                Attribute[] attributes)
            {
                // Get the default property descriptors from the base class
                PropertyDescriptorCollection propertyDescriptors =
                    base.GetProperties(attributes);

                // Get a reference to the model element that is being described.
                ExampleElement source = this.ModelElement as ExampleElement;

                //Add the descriptor for the tracking property.
                if (source != null)
                {
                    DomainPropertyInfo domainProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.NamespaceDomainPropertyId);

                    DomainPropertyInfo trackingProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);

                    // Define attributes for the tracking property so that the
                    // Properties window displays the property correctly.
                    Attribute[] attr = new Attribute[] {
                        new DisplayNameAttribute("Element Namespace"),
                        new DescriptionAttribute("The namespace of the element."),
                        new CategoryAttribute("Tracking Properties"),
                    };

                    propertyDescriptors.Add(new TrackingPropertyDescriptor(
                        source, domainProperty, trackingProperty, attr));
                }

                // Return the property descriptors for this element
                return propertyDescriptors;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-package"></a>パッケージのカスタム コードを追加します。

生成されたコード ExampleElement ドメイン クラスの型説明プロバイダーを定義します。ただし、この型説明プロバイダーを使用する DSL に指示するコードを追加する必要があります。

1.  Package.cs ファイルに次のコードを追加します。

    ```csharp
    using System.ComponentModel;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // Override the default Initialize method.
        internal sealed partial class TrackingPropertyDSLPackage
        {
            protected override void Initialize()
            {
                // Add the custom type descriptor for the ExampleElement type.
                TypeDescriptor.AddProvider(
                    new ExampleElementTypeDescriptionProvider(),
                    typeof(ExampleElement));

                base.Initialize();
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-model"></a>モデルのカスタム コードを追加します。

実装、`GetCustomElementsValue`のメソッド、`ExampleModel`ドメイン クラスです。

> [!NOTE]
> DSL ツールを生成するコード`ExampleModel`呼び出し`GetCustomElementsValue`。 ただし、DSL ツールは、メソッドを実装するコードを生成できません。

定義する、`GetCustomElementsValue`メソッドの計算 CustomElements プロパティのロジックを提供する`ExampleModel`です。 このメソッドの数をカウントする`ExampleElement`を追跡プロパティをユーザーが更新された値を持ち、モデル内の合計の要素の割合としてこの数を表す文字列を返しますの Namespace を持つドメイン クラスです。

さらに、追加、`OnDefaultNamespaceChanged`メソッドを`ExampleModel`、オーバーライド、`OnValueChanged`のメソッド、`DefaultNamespacePropertyHandler`のクラスを入れ子になった`ExampleModel`を呼び出す`OnDefaultNamespaceChanged`です。

追跡プロパティ、Namespace を計算に使用するために DefaultNamespace プロパティ`ExampleModel`すべて通知する必要があります`ExampleElement`ドメイン クラスに DefaultNamespace の値が変更されたことです。

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>追跡対象のプロパティのプロパティのハンドラーを変更するには

1.  ExampleModel.cs ファイルに次のコードを追加します。

    ```csharp
    using System.Linq;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        public partial class ExampleModel
        {
            public string GetCustomElementsValue()
            {
                if (this.Elements.Count == 0) return "0/0";

                int number = this.Elements.Count(e => !e.IsNamespaceTracking);
                return string.Format("{0}/{1}", number, this.Elements.Count);
            }

            #region Value changed handler for the tracked property

            // When a tracked property changes, it needs to notify all of the properties
            // that track it.

            /// <summary>Called by the DefaultNamespace property value handler when the
            /// DefaultNamespace property changes.</summary>
            /// <param name="oldValue">The previous value of the property.</param>
            /// <param name="newValue">The new value of the property.</param>
            protected virtual void OnDefaultNamespaceChanged(
                string oldValue, string newValue)
            {
                // Use the helper class to notify all of the elements in the model
                // that the default namespace has changed.
                TrackingHelper.UpdateTrackingCollectionProperty(
                    this.Store,
                    this.Elements,
                    ExampleElement.NamespaceDomainPropertyId,
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);
            }

            // Update the change handler for the DefaultNamespace property.
            internal sealed partial class DefaultNamespacePropertyHandler
            {
                /// <summary>Called when the DefaultNamespace property changes.</summary>
                /// <param name="element">The model element that has the property that
                /// changed.</param>
                /// <param name="oldValue">The previous value of the property.</param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleModel element, string oldValue, string newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);

                    if (!element.Store.InUndoRedoOrRollback)
                    {
                        element.OnDefaultNamespaceChanged(oldValue, newValue);
                    }
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-for-the-tracking-property"></a>追跡プロパティのカスタム コードを追加します。

追加、`CalculateNamespace`メソッドを`ExampleElement`ドメイン クラスです。

計算 CustomElements プロパティのロジックを提供するこのメソッドを定義する`ExampleModel`です。 このメソッドの数をカウントする`ExampleElement`を追跡は、更新されたプロパティの Namespace を持つドメイン クラスによって、ユーザー状態をモデル内の合計の要素の割合としてこの数を表す文字列を返します。

また、記憶域とを取得および設定を Namespace カスタム ストレージ プロパティのメソッドを追加、`ExampleElement`ドメイン クラスです。

> [!NOTE]
> DSL ツールを生成するコード`ExampleModel`get を呼び出すメソッドと set メソッドです。 ただし、DSL ツールがメソッドを実装するコードを生成しません。

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>カスタム型記述子のメソッドを追加するには

1.  NamespaceTrackingProperty.cs ファイルに次のコードを追加します。

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the domain class that has the tracking property, add the caluclation
        // for when the property is tracking.
        public partial class ExampleElement
        {
            /// <summary>Calculates the actual value of the property when it is
            /// tracking.</summary>
            /// <returns>The value of the tracking property when it is
            /// tracking.</returns>
            /// <remarks>Making this method virtual allows child classes to modify
            /// the calculation. This method does not need to perform validation, as
            /// its caller handles validation prior to calling this method.
            /// <para>In this case, the tracking value depends on the default namespace
            /// property of the parent model.</para></remarks>
            protected virtual string CalculateNamespace()
            {
                return this.ExampleModel.DefaultNamespace;
            }

            #region Tracking property implementation

            // Implement the Namespace domain property of the ExampleElement domain class,
            // and update the IsNamespaceTracking domain property value handler.

            /// <summary>Storage for the Namespace property.</summary>
            private string namespaceStorage;

            /// <summary>Gets the value of the Namespace property.</summary>
            /// <returns>The value of the Namespace property.</returns>
            private string GetNamespaceValue()
            {
                // Only retrieve the tracked value if the store is not in the
                // middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!loading && this.IsNamespaceTracking)
                {
                    try
                    {
                        return this.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                        return default(string);
                    }
                    catch (Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                        else
                        {
                            return default(string);
                        }
                    }
                }

                return namespaceStorage;
            }

            /// <summary>Sets the value of the Namespace property.</summary>
            /// <param name="value">The new value for the property.</param>
            private void SetNamespaceValue(string value)
            {
                namespaceStorage = value;

                // Only update the state of the tracking property if the store is
                // not in the middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!this.Store.InUndoRedoOrRollback && !loading)
                {
                    this.IsNamespaceTracking = false;
                }
            }

            // Update the default behavior of the ExampleElement.IsNamespaceTracking
            // domain property value handler.
            internal sealed partial class IsNamespaceTrackingPropertyHandler
            {
                /// <summary>Called after the IsNamespaceTracking property changes.
                /// </summary>
                /// <param name="element">The model element that has the property
                /// that changed.</param>
                /// <param name="oldValue">The previous value of the property.
                /// </param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleElement element, Boolean oldValue, Boolean newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);
                    if (!element.Store.InUndoRedoOrRollback && newValue)
                    {
                        DomainPropertyInfo propInfo =
                            element.Store.DomainDataDirectory.GetDomainProperty(
                                ExampleElement.NamespaceDomainPropertyId);
                        propInfo.NotifyValueChange(element);
                    }
                }

                /// <summary>Performs the reset operation for the IsNamespaceTracking
                /// property for a model element.</summary>
                /// <param name="element">The model element that has the property
                /// to reset.</param>
                internal void ResetValue(ExampleElement element)
                {
                    object calculatedValue = null;

                    try
                    {
                        calculatedValue = element.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                    }
                    catch (System.Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                    }

                    if ((calculatedValue != null
                        && object.Equals(element.Namespace, calculatedValue)))
                    {
                        element.isNamespaceTrackingPropertyStorage = true;
                    }
                }

                /// <summary>Method to set IsNamespaceTracking to false so that this
                /// instance of this tracking property is not storage-based.
                /// </summary>
                /// <param name="element">The element on which to reset the property
                /// value.</param>
                internal void PreResetValue(ExampleElement element)
                {
                    // Force the IsNamespaceTracking property to false so that the value
                    // of the Namespace property is retrieved from storage.
                    element.isNamespaceTrackingPropertyStorage = false;
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-to-support-serialization"></a>シリアル化をサポートするカスタム コードを追加します。

XML シリアル化のカスタムの読み込み後の動作をサポートするためにコードを追加します。

> [!NOTE]
> DSL ツールが呼び出しを生成するコード、`OnPostLoadModel`と`OnPostLoadModelAndDiagram`メソッドです。 ただし、DSL ツールがこれらのメソッドを実装するコードを生成しません。

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>カスタムの読み込み後の動作をサポートするためにコードを追加するには

1.  Serialization.cs ファイルに次のコードを追加します。

    ```csharp
    using System;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        #region Helper classes for maintaining state while the store is serializing.

        public abstract partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Reset the tracking state properties to their natural values
            /// based on comparing storage with calculation.</summary>
            /// <param name="store">The store that contains this model.</param>
            internal static void ResetTrackingProperties(Store store)
            {
                // Two passes required - one to set all elements to storage-based
                // then another to set some back to being tracking.
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.PreResetIsTrackingProperties();
                        continue;
                    }
                }
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.ResetIsTrackingProperties();
                        continue;
                    }
                }
            }
        }

        // Add the pre-reset and reset methods for the model element.
        public partial class ExampleElement
        {
            /// <summary>Calls the pre-reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void PreResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);
            }

            /// <summary>Calls the reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void ResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);
            }
        }

        #endregion

        #region Custom serialization code

        // To the serialization helper for the TrackingPropertyDSL class, add post
        // load handlers to bind the tracking property to the serialization process.
        // These handlers manage the tracking states and property values when the
        // model is serialized and deserialized.
        public partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Customize model loading.</summary>
            /// <param name="serializationResult">The serialization result from the
            /// load operation.</param>
            /// <param name="partition">The partition in which the new
            /// instance was created.</param>
            /// <param name="fileName">The name of the file from which the
            /// instance was deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.
            /// </param>
            private void OnPostLoadModel(
                SerializationResult serializationResult,
                Partition partition,
                string fileName,
                ExampleModel modelRoot)
            {
            }

            /// <summary>Customize model and diagram loading.</summary>
            /// <param name="serializationResult">Stores serialization result from
            /// the load operation.</param>
            /// <param name="modelPartition">Partition in which the new
            /// instance will be created.</param>
            /// <param name="modelFileName">Name of the file from which the
            /// instance will be deserialized.</param>
            /// <param name="diagramPartition">Partition in which the new
            /// diagram instance will be created.</param>
            /// <param name="diagramFileName">Name of the file from which the
            /// diagram instance will be deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.</param>
            /// <param name="diagram">The diagram matching the modelRoot.</param>
            private void OnPostLoadModelAndDiagram(
                SerializationResult serializationResult,
                Partition modelPartition,
                string modelFileName,
                Partition diagramPartition,
                string diagramFileName,
                ExampleModel modelRoot,
                TrackingPropertyDSLDiagram diagram)
            {
                Debug.Assert(modelPartition != null);
                Debug.Assert(modelPartition.Store != null);

                // Tracking properties need to be set up according to whether the
                // serialization matches the calculated values.
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(
                    modelPartition.Store);
            }
        }

        #endregion
    }
    ```

## <a name="test-the-language"></a>言語をテストします。

ビルドして実行 DSL デザイナーの新しいインスタンスを次の手順では[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]追跡プロパティが正しく動作していることを確認することができるようにします。

1.  **ビルド** メニューのをクリックして**ソリューションのリビルド**です。

2.  **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。

     試験的ビルド[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]開きます、**デバッグ**ソリューションで、空のテスト ファイルが含まれています。

3.  **ソリューション エクスプ ローラー**デザイナーで開く Test.trackingPropertyDsl ファイルをダブルクリックし、デザイン画面をクリックします。

     注意、**プロパティ**の図では、ウィンドウ、 **Default Namespace**プロパティは**に DefaultNamespace**、および**カスタム要素**プロパティは**0/0**です。

4.  ドラッグ、 **ExampleElement**から要素を**ツールボックス**ダイアグラム サーフェイスにします。

5.  **プロパティ**、要素のウィンドウ、**要素 Namespace**プロパティから値を変更して**に DefaultNamespace**に**OtherNamespace**です。

     注意して、値の**要素 Namespace**太字で表示されています。

6.  **プロパティ**ウィンドウを右クリックして**要素 Namespace**、クリックして**リセット**です。

     プロパティの値に変更されます**に DefaultNamespace**、し、値は通常フォントで表示されます。

     右クリック**要素 Namespace**もう一度です。 **リセット**プロパティが現在の追跡の状態であるために、コマンドが無効になります。

7.  別のドラッグ**ExampleElement**から、**ツールボックス**ダイアグラム領域で、変更をその**要素 Namespace**に**OtherNamespace**です。

8.  デザイン画面をクリックします。

     **プロパティ**ウィンドウ図では、値を**カスタム要素**現在**1/2**です。

9. 変更**Default Namespace**からダイアグラムの**に DefaultNamespace**に**NewNamespace**です。

     **Namespace**の最初の要素の追跡、 **Default Namespace**プロパティ、一方、 **Namespace** 2 番目の要素値を保持する、ユーザーが更新されたの**OtherNamespace**です。

10. ソリューションを保存し、実験用のビルドを閉じます。

## <a name="next-steps"></a>次の手順

プロパティの 1 つ以上の追跡を使用するか、1 つ以上の DSL の追跡のプロパティを実装する場合は、各追跡プロパティをサポートするための一般的なコードを生成するテキスト テンプレートを作成することができます。 テキスト テンプレートの詳細については、次を参照してください。[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)です。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)
- [方法: ドメイン固有言語ソリューションを作成する](../modeling/how-to-create-a-domain-specific-language-solution.md)
