---
title: Visual Studio API を使用して UML モデルを開く |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: e92ece9a8097071c8d8cef5b77ca9fdb242d677f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292709"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>Visual Studio API を使用して UML モデルを開く
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

API を使って、Visual Studio のユーザー インターフェイスでモデルと図を開くこともできます。  
  
 モデルをユーザーに表示せずに、プログラム コードでモデルの読み込みのみを行う場合は、次の方法を使用できます。  
  
-   Visual Studio モデル バスでは、モデルおよびモデル内の要素にアクセスすることができ、あるモデルと別のモデル間のリンクを生成する標準的な方法が提供されます。 詳細については、次を参照してください。[を他のモデルおよびツールとの統合の UML モデル](../modeling/integrate-uml-models-with-other-models-and-tools.md)します。  
  
-   読み取り専用モードでモデルを開くことができます。 詳細については、次を参照してください。[プログラム コードで UML モデルを読み取る](../modeling/read-a-uml-model-in-program-code.md)します。  
  
##  <a name="Showing"></a> Visual Studio でモデルおよびダイアグラムを開く  
 ユーザー インターフェイスでモデルを開くには、標準の Visual Studio API `EnvDTE.DTE` を使用します。 モデリング プロジェクト項目に対して実行できる便利なキャストが 2 つあります。  
  
-   プロジェクトがモデリング プロジェクトの場合で、そのプロジェクトが現在の AppDomain に読み込まれている場合、`EnvDTE.Project` と `IModelingProject` との間でキャストを行うことができます。  
  
-   項目が UML 図の場合、`EnvDTE.ProjectItem` と `IDiagramContext` との間でキャストを行うことができます。  
  
 以降の例の場合、プロジェクトは次の参照をインポートする必要があります。  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
-   Microsoft.VisualStudio.Modeling.Sdk.[バージョン]  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[バージョン]  
  
-   Microsoft.VisualStudio.Shell.Immutable.[バージョン]  
  
-   Microsoft.VisualStudio.Uml.Interfaces  
  
-   System.ComponentModel.Composition  
  
 この例では、Visual Studio で UML モデルを開きます。  
  
```  
using EnvDTE; // Visual Studio API for loading diagrams  
using   
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;    
   // for ICommandExtension and other handler types  
using Microsoft.VisualStudio.Uml.Classes;   
   // for basic UML types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // for model construction methods  
using EnvDTE;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;  
Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram   
...  
```  
  
 Visual Studio 拡張では、以下の宣言を行うことで、ホスト サービス プロバイダーへのアクセス権を取得できます。  
  
```  
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}  
...  
```  
  
 メソッドで、プロジェクト (たとえば、現在のプロジェクト) にアクセスできます。  
  
```  
DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;  
IModelingProject modelingProject = project as IModelingProject;  
if (modelingProject == null) return; // not a modeling project  
  
// Access the model's store and contents.  
IModelStore store = modelingProject.Store;  
foreach (IElement element in store.Root.OwnedElements) {...}  
  
// Open all the project's diagrams.  
foreach (ProjectItem item in project.ProjectItems)  
{   
     IDiagramContext modelingItem = item as IDiagramContext;  
     if (modelingItem == null)  
         continue; // not a model diagram  
     IDiagram diagram = modelingItem.CurrentDiagram;  
     if (diagram == null)  
     {  
        // Diagram is closed. Open it.  
        item.Open().Activate();  
        diagram = modelingItem.CurrentDiagram;  
     }  
     // Access the shapes.  
     foreach (IShape<IElement> shape   
               in diagram.GetChildShapes<IElement>())  
     {  
       IElement displayedElement = shape.Element;  
       ...  
     }  
   }  
}   
```  
  
## <a name="see-also"></a>関連項目  
 [UML API を使用したプログラミング](../modeling/programming-with-the-uml-api.md)   
 [UML モデルと図の拡張](../modeling/extend-uml-models-and-diagrams.md)



