---
title: Managed Package Framework を使用して、プロジェクトの種類 (c#) を実装する |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72d2ce8d817ab0d01a1a54f5e001165cd943c478
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533487"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>マネージド パッケージ フレームワークを使用したプロジェクト タイプの実装 (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロジェクトの種類 (c#) 用 Managed Package Framework を使用して](https://docs.microsoft.com/visualstudio/extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp)します。  
  
マネージ パッケージ フレームワーク (MPF) は、c# クラスを使用するか、独自のプロジェクトの種類を実装するために継承することができますを提供します。 MPF は取り込んだら、プロジェクトの種類の詳細の実装に専念する多くの Visual Studio に提供するため、プロジェクトの種類が必要ですが、インターフェイスを実装します。  
  
## <a name="using-the-mpf-project-source-code"></a>MPF プロジェクト ソース コードを使用します。  
 Managed Package Framework (MPFProj) プロジェクトを作成して、新しいプロジェクト システムを管理するためのヘルパー クラスを提供します。 MPF の他のクラスとは異なりプロジェクトのクラスは Visual Studio に付属するアセンブリに含まれていません。 ソース コードとしてプロジェクトのクラスを提供する代わりに、 [2013 のプロジェクトの MPF](http://mpfproj12.codeplex.com)します。  
  
 VSPackage ソリューションには、このプロジェクトを追加するには、次の操作を行います。  
  
1.  MPFProj ファイルをダウンロード*MPFProjectDir*します。  
  
2.  *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file、次のブロックを変更します。  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  VSPackage プロジェクトを作成します。  
  
2.  VSPackage プロジェクトをアンロードします。  
  
3.  VSPackage の .csproj ファイルを編集する前に、次のブロックを追加することで`<Import>`ブロック。  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  プロジェクトを保存します。  
  
2.  VSPackage ソリューションを閉じてから。  
  
3.  VSPackage プロジェクトを再度開きます。 ProjectBase をという名前の新しいディレクトリを表示する必要があります。  
  
4.  VSPackage プロジェクトに次の参照を追加します。  
  
     Microsoft.Build.Tasks.4.0  
  
5.  プロジェクトをビルドします。  
  
## <a name="hierarchy-classes"></a>クラスの階層  
 次の表では、プロジェクト階層をサポートしている、MPFProj でクラスを示します。 詳細については、次を参照してください。[階層と選択](../../extensibility/internals/hierarchies-and-selection.md)します。  
  
|クラス名|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>ドキュメント処理クラス  
 次の表では、ドキュメントの処理をサポートしている MPF でクラスを示します。 詳細については、次を参照してください。[とプロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)します。  
  
|クラス名|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>構成と出力クラス  
 次の表では、プロジェクトの種類のデバッグとリリースでは、プロジェクト出力のコレクションなどの複数の構成をサポートできる MPF クラスを示します。 詳細については、次を参照してください。[構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)します。  
  
|クラス名|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>オートメーションのサポート クラス  
 次の表は、プロジェクトの種類のユーザーがアドインを記述できるように、オートメーションをサポートしている MPF でクラスを一覧表示します。  
  
|クラス名|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>プロパティ クラス  
 次の表に示します、MPF をプロジェクトの種類のクラスは、ユーザーが参照およびプロパティ ブラウザーで変更できるプロパティを追加します。  
  
|クラス名|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|

