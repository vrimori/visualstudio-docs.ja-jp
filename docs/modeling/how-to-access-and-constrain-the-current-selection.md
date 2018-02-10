---
title: "方法: アクセスし、現在の選択範囲を制限する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 81036e04abc9eac2cbed2879839e95cce52166fc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>方法: 現在の選択項目を表示および制限する
ドメイン固有言語のコマンドまたはジェスチャ ハンドラーを記述するときに、ユーザーを右クリックした要素を指定できます。 一部のシェイプまたはフィールドも選択されないようにできます。 たとえば、ユーザーには、アイコン デコレータがクリックすると、それを含む図形が選択されている代わりに配置できます。 この方法の選択内容を制限すると、ハンドラーを記述する必要があるの回数が減ります。 またやすく、ユーザーに、デコレータを回避することがなく、図形内をクリックできます。  
  
## <a name="accessing-the-current-selection-from-a-command-handler"></a>コマンド ハンドラーから現在の選択範囲にアクセスします。  
 ドメイン固有言語のコマンド セット クラスには、カスタム コマンドのコマンド ハンドラーが含まれています。 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 、ドメイン固有言語のコマンド セット クラスの派生元のクラスは、現在の選択範囲にアクセスするため、いくつかのメンバーを提供します。  
  
 コマンド ハンドラーは、コマンドによって、モデル デザイナー、モデル エクスプ ローラーで、または作業中のウィンドウで選択を必要があります。  
  
#### <a name="to-access-selection-information"></a>選択範囲の情報にアクセスするには  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>クラスは、現在の選択範囲にアクセスするために使用する次のメンバーを定義します。  
  
    |メンバー|説明|  
    |------------|-----------------|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> メソッド|返します`true`場合は、モデル デザイナーで選択した要素のいずれかのコンパートメントの図形です。 それ以外の場合、`false`です。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> メソッド|返します`true`ダイアグラムがモデル デザイナーで選択されている、それ以外の場合`false`です。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> メソッド|返します`true`1 つの要素がモデル デザイナーで選択されている、それ以外の場合は`false`します。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> メソッド|返します`true`1 つの要素が作業中のウィンドウで選択されている、それ以外の場合は`false`します。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> プロパティ|モデル デザイナーで選択されている要素の読み取り専用コレクションを取得します。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> プロパティ|作業中のウィンドウで選択されている要素の読み取り専用コレクションを取得します。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> プロパティ|モデル デザイナーで、選択範囲の主な要素を取得します。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> プロパティ|アクティブ ウィンドウで、選択範囲の主な要素を取得します。|  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A>のプロパティ、<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>クラスへのアクセスを提供する、<xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>モデル デザイナー ウィンドウを表し、モデル デザイナーで選択した要素に追加のアクセスを提供するオブジェクト。  
  
3.  さらに、生成されたコードは、エクスプ ローラー ツール ウィンドウのプロパティを定義し、コマンドで、エクスプ ローラーの選択のプロパティは、ドメイン固有言語のクラスを設定します。  
  
    -   エクスプ ローラー ツール ウィンドウのプロパティは、ドメイン固有言語のエクスプ ローラー ツール ウィンドウ クラスのインスタンスを返します。 エクスプ ローラー ツール ウィンドウ クラスの派生元の<xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>クラスし、ドメイン固有言語モデル エクスプ ローラーを表します。  
  
    -   `ExplorerSelection`プロパティは、ドメイン固有言語モデル エクスプ ローラー ウィンドウで選択した要素を返します。  
  
## <a name="determining-which-window-is-active"></a>どのウィンドウがアクティブなを確認します。  
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>インターフェイスには、シェルで現在選択状態へのアクセスを提供するメンバーを定義します。 取得することができます、<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>オブジェクトから、パッケージ クラスか、コマンド セットのクラスを通じてドメイン固有言語、`MonitorSelection`の各基本クラスで定義されたプロパティ。 パッケージ クラスの派生元の<xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>から派生したクラス、およびコマンドの set クラス、<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>クラスです。  
  
#### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>コマンド ハンドラーを判別するのにはどのような種類のウィンドウがアクティブ  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A>のプロパティ、<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>クラスを返します、<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>シェルで現在選択状態へのアクセスを提供するオブジェクト。  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A>のプロパティ、<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>インターフェイスは、アクティブなウィンドウから異なる可能性があるアクティブな選択コンテナーを取得します。  
  
3.  コマンドを次のプロパティを設定クラスをアクティブなウィンドウの種類を決定するドメイン固有言語を追加します。  
  
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
  
## <a name="constraining-the-selection"></a>選択範囲を制限します。  
 選択ルールを追加すると、ユーザーがモデルの要素を選択したときにどの要素が選択を制御できます。 たとえば、要素の数を 1 つの単位として処理するユーザーを許可するのには、選択ルールを使用できます。  
  
#### <a name="to-create-a-selection-rule"></a>選択ルールを作成するには  
  
1.  DSL プロジェクトでカスタム コード ファイルを作成します。  
  
2.  派生した選択ルール クラスを定義、<xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>クラスです。  
  
3.  上書き、<xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A>クラスのメソッド、選択ルールの選択条件を適用します。  
  
4.  ClassDiagram クラスの部分クラス定義をカスタム コード ファイルに追加します。  
  
     `ClassDiagram`クラスから派生します<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>クラスし、は、生成されたコード ファイル、Diagram.cs、DSL プロジェクト内で定義されています。  
  
5.  上書き、<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A>のプロパティ、`ClassDiagram`カスタム選択ルールを返すためにします。  
  
     既定の実装、<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A>プロパティが選択範囲を変更しない選択規則オブジェクトを取得します。  
  
### <a name="example"></a>例  
 次のコード ファイルでは、最初に選択したドメインの図形のそれぞれのインスタンスをすべて選択範囲が広がる選択ルールを作成します。  
  
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
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>