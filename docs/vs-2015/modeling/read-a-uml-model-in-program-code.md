---
title: プログラム コードで UML モデルを読み取る |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 62355c8b934b152aae8d3a4102432d2eb0553473
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721243"
---
# <a name="read-a-uml-model-in-program-code"></a>プログラム コードで UML モデルを読み取る
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML API を使用して、UML モデルおよび UML 図を読み込むことができます。  
  
##  <a name="Reading"></a> プログラム コードでのモデルの読み込み  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ウィンドウに表示せずにモデルのコンテンツにアクセスするには、`ModelingProject.LoadReadOnly()` を使用します。  
  
 例:  
  
```  
using Microsoft.VisualStudio.Uml.Classes;   
               // for IElement  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;   
               // for ModelingProject  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
               // for IModelStore  
...   
string projectPath = @"C:\MyProjectFolder\MyProject.modelproj";  
using (IModelingProjectReader projectReader =  
           ModelingProject.LoadReadOnly(projectPath))  
{  
   IModelStore store = projectReader.Store;  
   foreach (IClass umlClass in store.AllInstances<IClass>())  
   {   
       ...  
   }  
}  
```  
  
 図の中の図形を読み込むには、プロジェクトを読み込んでから図を読み込む必要があります。  
  
 例:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram  
...  
foreach (string diagramFile in projectReader. DiagramFileNames)  
{   
  IDiagram diagram = projectReader.LoadDiagram(diagramFile);  
  foreach (IShape<IElement> shape   
         in diagram.GetChildShapes<IElement>())  
  { ... }  
}  
```  
  
## <a name="alternative-methods"></a>その他の方法  
 多くのアプリケーション、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Modelbus では参照モデル内の要素を保全性とこのトピックで説明する方法よりも高い柔軟性をできます。 同じモデル、または別のモデル内の任意の要素をリンクするための、標準的な方法を使用できます。 詳細については、次を参照してください。[を他のモデルおよびツールとの統合の UML モデル](../modeling/integrate-uml-models-with-other-models-and-tools.md)します。  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API を使用して、ユーザー インターフェイスでモデルおよび図を開くこともできます。 詳細については、次を参照してください。 [Visual Studio API を使用して UML モデルを開く](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)します。  
  
##  <a name="Standalone"></a> スタンドアロン アプリケーション  
 前のセクションの例は、Visual Studio 拡張機能で動作します。 スタンドアロン アプリーションでモデルを読み込むこともできますが、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクトにいくつかの参照を追加する必要があります。  
  
> [!NOTE]
>  スタンドアロン アプリケーションでモデルを読み込む方法については、製品の今後のバージョンで変更される可能性があります。 現在のバージョンで使用できる機能のいくつかは、将来のバージョンでは利用できなくなる可能性があります。  
  
#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>スタンドアロン アプリケーションのモデルを読み込むための参照を追加するには  
  
1. ソリューション エクスプ ローラーでプロジェクトをアプリケーションを構築し、 をクリックしを右クリックして**プロパティ**します。 プロパティ エディターでの**アプリケーション**タブで、設定**ターゲット フレームワーク**に必要な .NET Framework のバージョン。  
  
2. UML モデルにアクセスするために必要な [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] 参照を追加します。  
  
   -   Microsoft.VisualStudio.Uml.Interfaces.dll  
  
   -   Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
3. 次のプロジェクト参照を追加すると、前のセクションで示した参照に加えて**\Program Files\Microsoft Visual Studio [バージョン] \Common7\IDE\PrivateAssemblies**:  
  
   - Microsoft.VisualStudio.Uml.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll  
  
     アプリケーションで図を読み込む場合は、次の参照が必要になることもあります。  
  
   - Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll  
  
## <a name="see-also"></a>関連項目  
 [UML API を使用したプログラミング](../modeling/programming-with-the-uml-api.md)   
 [UML モデルと図の拡張](../modeling/extend-uml-models-and-diagrams.md)



