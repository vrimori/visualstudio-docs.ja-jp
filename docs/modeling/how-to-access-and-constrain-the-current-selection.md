---
title: "方法: 現在の選択項目を表示および制限する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメイン固有言語, アクセス (現在の選択項目に)"
ms.assetid: 2990981e-dfae-416f-b0d0-7197f1242dfa
caps.latest.revision: 14
caps.handback.revision: 14
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 方法: 現在の選択項目を表示および制限する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ドメイン固有言語のコマンドまたはジェスチャ ハンドラーを記述する場合は、ユーザーが右クリック、どのような要素を指定できます。 選択されている一部のシェイプまたはフィールドを防ぐことができます。 たとえば、ユーザーには、アイコン デコレータがクリックすると、それを含んでいる図形が選択されている代わりに配置できます。 この方法の選択内容の制約を定義すると、ハンドラーを記述する必要があるの回数が減ります。 簡単ことがユーザーのデコレータを回避することがなく、図形内をクリックできます。  
  
## コマンド ハンドラーから現在の選択項目にアクセスします。  
 ドメイン固有言語のコマンド セット クラスには、カスタムのコマンドに対するコマンド ハンドラーが含まれています。<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 、ドメイン固有言語のコマンド セット クラスの派生元のクラスは、現在の選択項目にアクセスするため、いくつかのメンバーを提供します。  
  
 コマンド ハンドラーは、コマンドによって、モデル デザイナー、モデル エクスプ ローラーで、またはアクティブなウィンドウで選択したを必要があります。  
  
#### 選択範囲の情報にアクセスするには  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> クラスは、現在の選択項目にアクセスするために使用する次のメンバーを定義します。  
  
    |メンバー|説明|  
    |----------|--------|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> メソッド|返します。 `true` コンパートメント シェイプ; は、モデル デザイナーで選択した要素のいずれかの場合は、それ以外の場合、 `false`です。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> メソッド|返します。 `true` 場合は、ダイアグラムで、モデル デザイナーで選択されているそれ以外の場合、 `false`です。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> メソッド|返します。 `true` 場合、1 個の要素は、モデル デザイナーで選択されているそれ以外の場合、 `false`です。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> メソッド|返します。 `true` 場合は 1 個の要素は、アクティブなウィンドウで選択されているそれ以外の場合、 `false`です。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> プロパティ|モデル デザイナーで選択した要素の読み取り専用コレクションを取得します。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> プロパティ|作業中のウィンドウで選択した要素の読み取り専用コレクションを取得します。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> プロパティ|モデル デザイナーでは、選択範囲の主要な要素を取得します。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> プロパティ|アクティブ ウィンドウで、選択範囲の主要な要素を取得します。|  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> のプロパティ、 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> クラスへのアクセスを提供する、 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> モデル デザイナー ウィンドウを表し、モデル デザイナーで選択した要素に追加のアクセスを提供するオブジェクト。  
  
3.  さらに、生成されたコードは、エクスプ ローラーのツール ウィンドウのプロパティを定義し、コマンドでエクスプ ローラー選択プロパティは、ドメイン固有言語のクラスを設定します。  
  
    -   エクスプ ローラーのツール ウィンドウのプロパティでは、ドメイン固有言語エクスプ ローラー ツールのウィンドウ クラスのインスタンスを返します。 エクスプ ローラー ツールのウィンドウ クラスの派生元の <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> クラスし、ドメイン固有言語のモデル エクスプ ローラーを表します。  
  
    -   `ExplorerSelection` プロパティは、ドメイン固有言語モデル エクスプ ローラーで選択した要素を返します。  
  
## どのウィンドウがアクティブなを決定します。  
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> インターフェイスには、シェルでは、現在の選択状態へのアクセスを提供するメンバーを定義します。 取得できます、 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> パッケージ クラスまたはから、ドメイン固有言語のコマンド セット クラスのいずれかからオブジェクトを `MonitorSelection` プロパティそれぞれの基本クラスで定義します。 パッケージ クラスの派生元の <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> クラス、およびコマンド セット クラスから派生した、 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> クラスです。  
  
#### コマンド ハンドラーを判別するのにはどのようなウィンドウの種類がアクティブ  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> のプロパティ、 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> クラスを返します。、 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> シェルでは、現在の選択状態へのアクセスを提供するオブジェクト。  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> のプロパティ、 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> インターフェイスはアクティブなウィンドウと異なるものになる可能性がアクティブな選択範囲のコンテナーを取得します。  
  
3.  コマンドには、次のプロパティを設定クラスのアクティブ ウィンドウの種類を確認するドメイン固有言語を追加します。  
  
    ```c#  
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
  
## 選択範囲を制限します。  
 選択ルールを追加すると、ユーザーがモデルの要素を選択したときにどの要素が選択されてを制御できます。 たとえば、要素の数を 1 つの単位として処理するユーザーを許可するのには、選択ルールを使用できます。  
  
#### 選択ルールを作成するには  
  
1.  DSL プロジェクトでカスタム コード ファイルを作成します。  
  
2.  派生した選択ルール クラスを定義、 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> クラスです。  
  
3.  オーバーライド、 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> 選択条件を適用する、選択ルール クラスのメソッドです。  
  
4.  カスタム コード ファイルに ClassDiagram クラスの部分クラス定義を追加します。  
  
     `ClassDiagram` クラスから派生する、 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> クラスし、は、生成されたコード ファイルを Diagram.cs、DSL プロジェクト内で定義されています。  
  
5.  オーバーライド、 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> のプロパティ、 `ClassDiagram` カスタム選択ルールを返すためにします。  
  
     既定の実装、 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> プロパティは、選択範囲を変更しない選択ルール オブジェクトを取得します。  
  
### 例  
 次のコード ファイルでは、最初に選択したドメインの図形のそれぞれのインスタンスをすべて選択範囲が広がる選択ルールを作成します。  
  
```c#  
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
  
## 参照  
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>