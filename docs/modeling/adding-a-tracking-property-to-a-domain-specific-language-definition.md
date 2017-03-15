---
title: "ドメイン固有言語定義に追跡プロパティの追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: 4aa47777-de75-4897-a423-a3c4426b4125
caps.latest.revision: 22
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
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
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 0d97770109a3c362f99a014829e694fc2e027196
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>ドメイン固有言語の定義への追跡プロパティの追加
このチュートリアルでは、ドメイン モデルに追跡プロパティを追加する方法を示します。  
  
 A*ドメインを追跡*プロパティは、ユーザーが更新できるが、その他のドメインのプロパティまたは要素の値を使用して計算される既定値を持つプロパティです。  
  
 たとえば、ドメイン固有言語ツール (DSL ツール) でのドメイン クラスのユーザー名を使用して計算される既定値を持つドメイン クラスのプロパティの表示名デザイン時に値を変更したり計算値にリセットできます。  
  
 このチュートリアルでは、モデルの既定の Namespace プロパティに基づく既定値を持つプロパティを追跡 Namespace を持つドメイン固有言語 (DSL) を作成します。 追跡のプロパティの詳細については、次を参照してください。[追跡プロパティを定義する](http://msdn.microsoft.com/en-us/0538b0e4-6221-4e7d-911a-b92cd622f0be)です。  
  
-   DSL ツールは、まずプロパティ記述子の追跡をサポートします。 ただし、DSL デザイナーを使用して、追跡プロパティの言語を追加することはできません。 したがって、定義して、tracking プロパティを実装するカスタム コードを追加する必要があります。  
  
 追跡プロパティが&2; つの状態: 追跡、およびユーザーによって更新されました。 追跡のプロパティでは、次の特徴があります。  
  
-   追跡状態の追跡プロパティの値が計算され、モデルの変更では、他のプロパティと値を更新します。  
  
-   更新済みの場合に、ユーザー状態を追跡プロパティの値には、ユーザー最後に設定するプロパティ値が保持されます。  
  
-   **プロパティ**ウィンドウで、**リセット**コマンド プロパティは、更新された場合にのみ、tracking プロパティが有効でユーザー状態。 **リセット**コマンドは、tracking プロパティを設定状態を追跡します。  
  
-   **プロパティ**ウィンドウ、追跡プロパティが追跡の状態、その値が通常のフォントで表示されます。  
  
-   **プロパティ**ウィンドウで、追跡プロパティが更新済みの場合、ユーザー状態では、その値が太字フォントで表示されます。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを開始する前に、これらのコンポーネントを最初にインストールする必要があります。  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-the-dsl-project"></a>DSL プロジェクトを作成します。  
 ドメイン固有言語のプロジェクトを作成します。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1.  ドメイン固有言語デザイナーのプロジェクトを作成します。 これに `TrackingPropertyDSL` という名前を付けます。  
  
2.  **ドメイン固有言語デザイナー ウィザード**、次のオプションを設定します。  
  
    1.  選択、 **MinimalLanguage**テンプレートです。  
  
    2.  ドメイン固有言語の既定の名前を使用して`TrackingPropertyDSL`します。  
  
    3.  モデル ファイルの拡張機能を設定`trackingPropertyDsl`します。  
  
    4.  モデル ファイルの既定のテンプレートのアイコンを使用します。  
  
    5.  この製品の名前を設定`Product Name`します。  
  
    6.  会社の名前を設定`Company Name`します。  
  
    7.  既定値を使用して、ソリューション内のプロジェクトのルート名前空間の`CompanyName.ProductName.TrackingPropertyDSL`です。  
  
    8.  アセンブリの厳密な名前キー ファイルを作成するウィザードを使用できます。  
  
    9. ソリューションの詳細を確認し、をクリックして**完了**DSL 定義プロジェクトを作成します。  
  
## <a name="customizing-the-default-dsl-definition"></a>既定の DSL 定義をカスタマイズします。  
 このセクションで、次の項目を格納する DSL 定義をカスタマイズします。  
  
-   モデルのすべての要素のプロパティを追跡 Namespace です。  
  
-   モデルの各要素に対してブール IsNamespaceTracking プロパティです。 このプロパティは追跡プロパティが追跡状態または更新されたのかどうかを指定してユーザー状態。  
  
-   モデルの既定の Namespace プロパティです。 このプロパティは、Namespace の追跡プロパティの既定値の計算に使用されます。  
  
-   モデルの計算 CustomElements プロパティです。 このプロパティには、カスタム名前空間を持つ要素の割合が示されます。  
  
#### <a name="to-add-the-domain-properties"></a>ドメインのプロパティを追加するには  
  
1.  DSL デザイナー内を右クリックし、 **ExampleModel**ドメイン クラスを指す**追加**、 をクリックし、**ドメイン プロパティがあり**します。  
  
    1.  Name プロパティを新しい`DefaultNamespace`します。  
  
    2.  **プロパティ**ウィンドウで、新しいプロパティの設定**既定値**に`DefaultNamespace`、設定と**型**に**文字列**します。  
  
2.  **ExampleModel**ドメイン クラスでをという名前のドメイン プロパティを追加`CustomElements`します。  
  
     **プロパティ**ウィンドウで、新しいプロパティの設定**種類**に**Calculated**します。  
  
3.  **ExampleElement**ドメイン クラスでをという名前のドメイン プロパティを追加`Namespace`します。  
  
     **プロパティ**ウィンドウで、新しいプロパティの設定**はブラウズ可能な**に**False**、設定と**種類**に**CustomStorage**します。  
  
4.  **ExampleElement**ドメイン クラスでをという名前のドメイン プロパティを追加`IsNamespaceTracking`します。  
  
     **プロパティ**ウィンドウで、新しいプロパティの設定**はブラウズ可能な**に**False**設定**既定値**に`true`、設定と**型**に**ブール**します。  
  
#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>図の要素と DSL 詳細を更新するには  
  
1.  DSL デザイナー内を右クリックし、 **ExampleShape**ジオメトリ シェイプを指す**追加**、クリックして**テキスト デコレータ**です。  
  
    1.  名前を新しいテキスト デコレータ`NamespaceDecorator`します。  
  
    2.  **プロパティ** ウィンドウのテキスト デコレータ設定**位置**に**InnerBottomLeft**します。  
  
2.  DSL デザイナーで接続する線を選択して、 **ExampleElement**クラスを**ExampleShape**図形です。  
  
    1.  **DSL 詳細**ウィンドウを選択して、**デコレータ マップ** タブをクリックします。  
  
    2.  **デコレータ**一覧で、 **NamespaceDecorator**、そのチェック ボックスをオンにし、**プロパティの表示**一覧で、 **Namespace**します。  
  
3.  **DSL エクスプ ローラー**、展開、**ドメイン クラス** フォルダーを右クリックし、 **ExampleElement**ノードをクリックして**ドメインの新しい型記述子の追加**します。  
  
    1.  展開、 **ExampleElement**ノードを**カスタム型記述子 (ドメイン型記述子)**ノードです。  
  
    2.  **プロパティ**ウィンドウで、ドメイン型記述子の設定**カスタム コード化された**に**True**します。  
  
4.  **DSL エクスプ ローラー**を選択、 **Xml Serialization Behavior**ノードです。  
  
    1.  **プロパティ**ウィンドウで、設定**カスタム Post ロード**に**True**します。  
  
## <a name="transforming-templates"></a>テンプレートを変換します。  
 これで、DSL のドメイン クラスとプロパティを定義する、プロジェクトのコードを再生成する DSL 定義を正しく変換できることを確認できます。  
  
#### <a name="to-transform-the-text-templates"></a>テキスト テンプレートを変換するには  
  
1.  **ソリューション エクスプ ローラー**ツールバーで、をクリックして**すべてのテンプレートの変換**します。  
  
2.  システムは、ソリューションのコードを再生成し、DslDefinition.dsl を保存します。 定義ファイルの XML 形式については、次を参照してください。 [DslDefinition.dsl ファイル](../modeling/the-dsldefinition-dsl-file.md)します。  
  
## <a name="creating-files-for-custom-code"></a>カスタム コードのファイルの作成  
 すべてのテンプレートを変換すると、システムは、Dsl および DslPackage プロジェクトにドメイン固有言語を定義するソース コードを生成します。 生成されるテキストに干渉することを回避できます、生成されたコード ファイルから個別のファイルでカスタム コードを記述します。  
  
 値と追跡プロパティの状態を維持するため、コードを記述する必要があります。 生成されたコードから、カスタム コードを区別することと、ファイル名前付けの競合を回避するは、サブフォルダーに個別に、カスタム コード ファイルを配置します。  
  
#### <a name="to-create-the-code-files"></a>コード ファイルを作成するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **DSL**プロジェクト をポイントして**追加**、クリックして**新しいフォルダー**します。 新しいフォルダーに名前を`CustomCode`します。  
  
2.  新しいを右クリックし**されるカスタム コード**フォルダーを指す**追加**、順にクリック**新しい項目の**です。  
  
3.  選択、**コード ファイル**テンプレートの設定、**名**に`NamespaceTrackingProperty.cs`、 をクリックし、 **ok**します。  
  
     NamespaceTrackingProperty.cs ファイルが作成され、編集用に開きます。  
  
4.  フォルダー内には、次のコード ファイルを作成します。 `ExampleModel.cs,``HelperClasses.cs`、 `Serialization.cs`、および`TypeDescriptor.cs`です。  
  
5.  **DslPackage**プロジェクトを作成しても、`CustomCode`フォルダーを追加、`Package.cs`コード ファイル。  
  
## <a name="adding-helper-classes-to-support-tracking-properties"></a>プロパティの追跡をサポートするヘルパー クラスを追加します。  
 HelperClasses.cs ファイルに追加、`TrackingHelper`と`CriticalException`クラスの次のようにします。 このチュートリアルの後半でこれらのクラスを参照します。  
  
#### <a name="to-add-the-helper-classes"></a>ヘルパー クラスを追加するには  
  
1.  HelperClasses.cs ファイルに次のコードを追加します。  
  
    ```c#  
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
  
## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>カスタム型記述子のカスタム コードを追加します。  
 実装、`GetCustomProperties`メソッドの型記述子を`ExampleModel`ドメイン クラスです。  
  
> [!NOTE]
>  カスタム型記述子の DSL ツールが生成されるコードが`ExampleModel`呼び出し`GetCustomProperties`。 ただし、DSL ツールは、メソッドを実装するコードを生成しません。  
  
 このメソッドを定義する、追跡と作成のプロパティを追跡 Namespace プロパティ記述子。 により、追跡プロパティの属性を提供することも、**プロパティ**プロパティを正しく表示するウィンドウです。  
  
#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>ExampleModel ドメイン クラスの型記述子を変更するには  
  
1.  TypeDescriptor.cs ファイルに次のコードを追加します。  
  
    ```c#  
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
 生成されたコード ExampleElement ドメイン クラスの型説明のプロバイダーを定義します。ただし、この型の説明のプロバイダーを使用する DSL に指示するコードを追加する必要があります。  
  
#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>カスタムの型記述子を使用する DSL パッケージを更新するには  
  
1.  Package.cs ファイルに次のコードを追加します。  
  
    ```c#  
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
  
## <a name="adding-custom-code-for-the-model"></a>モデルのカスタム コードを追加します。  
 実装、`GetCustomElementsValue`のメソッド、`ExampleModel`ドメイン クラスです。  
  
> [!NOTE]
>  DSL ツールが生成されるコードが`ExampleModel`呼び出し`GetCustomElementsValue`。 ただし、DSL ツールは、メソッドを実装するコードを生成しません。  
  
 定義する、`GetCustomElementsValue`メソッドの計算 CustomElements プロパティのロジックを提供する`ExampleModel`です。 このメソッドの数をカウントする`ExampleElement`追跡プロパティをユーザーに更新された値を持つをモデル内の合計の要素に対する比率としてこの数を表す文字列を返す Namespace のあるドメイン クラスです。  
  
 さらに、追加、`OnDefaultNamespaceChanged`メソッドを`ExampleModel`をオーバーライドし、`OnValueChanged`のメソッド、`DefaultNamespacePropertyHandler`のクラスを入れ子になった`ExampleModel`を呼び出す`OnDefaultNamespaceChanged`します。  
  
 DefaultNamespace プロパティを使用して、プロパティを追跡 Namespace を計算するので`ExampleModel`すべてに通知する必要があります`ExampleElement`DefaultNamespace の値が変更されたドメイン クラスです。  
  
#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>追跡対象のプロパティのプロパティ ハンドラーを変更するには  
  
1.  ExampleModel.cs ファイルに次のコードを追加します。  
  
    ```c#  
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
  
## <a name="adding-custom-code-for-the-tracking-property"></a>追跡プロパティのカスタム コードを追加します。  
 追加、`CalculateNamespace`メソッドを`ExampleElement`ドメイン クラスです。  
  
 計算 CustomElements プロパティのロジックを提供するこのメソッドを定義する`ExampleModel`です。 このメソッドの数をカウントする`ExampleElement`更新済みであるプロパティを追跡 Namespace のあるドメイン クラスによって、ユーザー状態をモデル内の合計の要素の割合としてこの数を表す文字列を返します。  
  
 さらに、追加、記憶域とメソッドを取得および設定の Namespace カスタム ストレージ プロパティ、`ExampleElement`ドメイン クラスです。  
  
> [!NOTE]
>  DSL ツールが生成されるコードが`ExampleModel`get を呼び出すメソッドと set メソッドです。 ただし、DSL Tools がメソッドを実装するコードを生成しません。  
  
#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>カスタム型記述子のメソッドを追加するには  
  
1.  NamespaceTrackingProperty.cs ファイルに次のコードを追加します。  
  
    ```c#  
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
  
## <a name="adding-custom-code-to-support-serialization"></a>シリアル化をサポートするためにカスタム コードを追加します。  
 XML シリアル化の後の読み込み時のカスタム動作をサポートするためにコードを追加します。  
  
> [!NOTE]
>  DSL ツールが呼び出しを生成するコード、`OnPostLoadModel`と`OnPostLoadModelAndDiagram`メソッドです。 ただし、DSL ツールがこれらのメソッドを実装するコードを生成しません。  
  
#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>カスタムの後の読み込み動作をサポートするためにコードを追加するには  
  
1.  Serialization.cs ファイルに次のコードを追加します。  
  
    ```c#  
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
  
## <a name="testing-the-language"></a>言語のテスト  
 次の手順は、ビルドを実行する DSL デザイナーの新しいインスタンスは[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]追跡プロパティが正しく動作していることを確認できるようにします。  
  
#### <a name="to-exercise-the-language"></a>言語を実行するには  
  
1.  **ビルド** メニューのをクリックして**ソリューションのリビルド**します。  
  
2.  **デバッグ** メニューのをクリックして**デバッグ開始**します。  
  
     実験用ビルド[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]が開き、**デバッグ**ソリューションで、空のテスト ファイルが含まれています。  
  
3.  **ソリューション エクスプ ローラー**をデザイナーで開く Test.trackingPropertyDsl ファイルをダブルクリックし、デザイン画面をクリックします。  
  
     ことに注意して、**プロパティ**、ダイアグラムのウィンドウ、 **Namespace の既定の**プロパティは、 **DefaultNamespace**、および**カスタム要素**プロパティは、 **0/0**します。  
  
4.  ドラッグ、 **ExampleElement**要素を**ツールボックス**ダイアグラム サーフェイスにします。  
  
5.  **プロパティ**、要素のウィンドウ、**要素 Namespace**プロパティには、値から変更**DefaultNamespace**に**OtherNamespace**します。  
  
     注意して、値の**要素 Namespace**太字で表示されています。  
  
6.  **プロパティ** ウィンドウを右クリックして**要素 Namespace**、 をクリックし、**リセット**します。  
  
     プロパティの値は**DefaultNamespace**、通常のフォントで示されている値。  
  
     右クリック**要素 Namespace**再度します。 **リセット**プロパティが現在の追跡の状態であるために、コマンドが無効になります。  
  
7.  別のドラッグ**ExampleElement**から、**ツールボックス**ダイアグラム領域で、変更をその**要素 Namespace**に**OtherNamespace**します。  
  
8.  デザイン画面をクリックします。  
  
     **プロパティ**図 の値のウィンドウ**カスタム要素**現在**1/2**します。  
  
9. 変更**既定 Namespace**からダイアグラムの**DefaultNamespace**に**NewNamespace**します。  
  
     **Namespace**最初の要素のトラックの**既定 Namespace**プロパティには、一方、 **Namespace**&2; 番目の要素、値を保持ユーザー更新の**OtherNamespace**します。  
  
10. ソリューションを保存、実験用ビルドを閉じてください。  
  
## <a name="next-steps"></a>次の手順  
 1 つ以上の追跡のプロパティを使用して、または&1; つ以上の DSL に追跡プロパティを実装する場合は、各追跡プロパティをサポートするための一般的なコードを生成するテキスト テンプレートを作成できます。 テキスト テンプレートの詳細については、次を参照してください。[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor></xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>   
 <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor></xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>   
 [ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)   
 [方法: ドメイン固有言語ソリューションを作成する](../modeling/how-to-create-a-domain-specific-language-solution.md)   

