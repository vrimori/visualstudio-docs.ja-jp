---
title: '方法: 現在の選択項目を表示および制限する'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 799e6fdc50cad91ebd5ee5081b1d80fa296f5a7c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947951"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>方法: 現在の選択項目を表示および制限する

ドメイン固有言語のコマンドまたはジェスチャ ハンドラーを記述するときに、どのような要素をユーザーが右クリックを確認できます。 一部のシェイプまたはフィールドも選択できないようにできます。 たとえば、ユーザーは、アイコン、デコレーターをクリックすると、それを含んでいる図形が選択されている代わりに配置できます。 この方法で選択範囲の制約は、ハンドラーを記述する必要があるの数を減らします。 簡単に、ユーザー、デコレーターを回避することがなく、図形内をクリックできます。

## <a name="access-the-current-selection-from-a-command-handler"></a>現在の選択コマンド ハンドラーからのアクセス

ドメイン固有言語のコマンド セット クラスには、カスタム コマンドに対するコマンド ハンドラーが含まれています。 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 、ドメイン固有言語のコマンド セット クラスの派生元のクラスは、現在の選択範囲にアクセスするため、いくつかのメンバーを提供します。

コマンド ハンドラーは、コマンドによって、モデル デザイナー、モデル エクスプ ローラーで、またはアクティブなウィンドウで選択を必要があります。

### <a name="to-access-selection-information"></a>選択範囲の情報にアクセスするには

1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>クラスは、現在の選択範囲へのアクセスに使用できる次のメンバーを定義します。

    |メンバー|説明|
    |-|-|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> メソッド|返します`true`場合は、モデル デザイナーで選択された要素のいずれかが、コンパートメント シェイプ。 それ以外の場合、`false`します。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> メソッド|返します`true`ダイアグラムがモデル デザイナーで選択した。 それ以外の場合`false`します。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> メソッド|返します`true`正確に 1 つの要素がモデル デザイナーで選択した。 それ以外の場合`false`します。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> メソッド|返します`true`正確に 1 つの要素が作業中のウィンドウで選択した。 それ以外の場合`false`します。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> プロパティ|モデル デザイナーで選択された要素の読み取り専用コレクションを取得します。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> プロパティ|アクティブなウィンドウで選択した要素の読み取り専用コレクションを取得します。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> プロパティ|モデル デザイナーでは、プライマリの選択範囲の要素を取得します。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> プロパティ|アクティブ ウィンドウには、プライマリの選択範囲の要素を取得します。|

2.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A>のプロパティ、<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>クラスへのアクセスを提供する、<xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>オブジェクトをモデル デザイナー ウィンドウを表し、モデル デザイナーで選択した要素の追加のアクセスを提供します。

3.  さらに、生成されたコードは、エクスプ ローラー ツール ウィンドウのプロパティを定義し、コマンドで、エクスプ ローラーの選択のプロパティは、ドメイン固有言語のクラスを設定します。

    -   エクスプ ローラー ツール ウィンドウのプロパティは、ドメイン固有言語エクスプ ローラー ツール ウィンドウ クラスのインスタンスを返します。 エクスプ ローラー ツール ウィンドウのクラスから派生、<xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>クラスし、ドメイン固有言語モデル エクスプ ローラーを表します。

    -   `ExplorerSelection`プロパティは、ドメイン固有言語モデル エクスプ ローラー ウィンドウで、選択した要素を返します。

## <a name="determine-which-window-is-active"></a>どのウィンドウがアクティブの決定します。

<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>インターフェイスには、シェルでは、現在の選択状態へのアクセスを提供するメンバーを定義します。 取得することができます、<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>パッケージ クラスまたはを通じてドメイン固有言語のコマンド セット クラスのいずれかからのオブジェクト、`MonitorSelection`それぞれの基本クラスで定義されたプロパティ。 パッケージ クラスから派生、<xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>から派生したクラス、およびコマンド セット クラス、<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>クラス。

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>コマンド ハンドラーを判別するのにはどのような種類のウィンドウがアクティブ

1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A>のプロパティ、<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>クラスを返します、 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> shell では、現在の選択状態へのアクセスを提供するオブジェクト。

2.  <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A>のプロパティ、<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>インターフェイスは、アクティブなウィンドウから異なる可能性があるアクティブな選択コンテナーを取得します。

3.  コマンドには、次のプロパティ設定クラスをアクティブ ウィンドウの種類を確認するドメイン固有言語を追加します。

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>選択範囲を制限します。

選択ルールを追加すると、ユーザーがモデル内の要素を選択する要素が選択されてを制御できます。 たとえば、要素の数を 1 つの単位として処理するユーザーを許可するのには、選択ルールを使用できます。

### <a name="to-create-a-selection-rule"></a>選択ルールを作成するには

1.  DSL プロジェクト内のカスタム コード ファイルを作成します。

2.  派生した選択ルール クラスを定義、<xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>クラス。

3.  上書き、<xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A>選択条件を適用する、選択ルール クラスのメソッド。

4.  カスタム コード ファイルに ClassDiagram クラスの部分クラス定義を追加します。

     `ClassDiagram`クラスから派生、<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>クラスし、DSL プロジェクトで生成されたコード ファイル、Diagram.cs で定義されます。

5.  オーバーライド、<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A>のプロパティ、`ClassDiagram`クラスをカスタム選択規則を返します。

     既定の実装、<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A>プロパティは、選択範囲を変更しない選択ルール オブジェクトを取得します。

### <a name="example"></a>例

次のコード ファイルは、選択項目を最初に選択したドメインの図形のそれぞれのすべてのインスタンスに展開された選択ルールを作成します。

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>