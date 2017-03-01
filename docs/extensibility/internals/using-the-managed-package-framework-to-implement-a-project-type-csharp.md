---
title: "マネージ パッケージ フレームワークを使用して、プロジェクトの種類 (c#) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: 1d70a70b942b3722ed61e1e8a2f2e54d96b916e4
ms.lasthandoff: 02/22/2017

---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>マネージ パッケージ フレームワークを使用して、プロジェクトの種類 (c#) を実装するには
管理されているパッケージ フレームワーク (MPF) は、c# クラスを使用するか、独自のプロジェクトの種類の実装の継承を提供します。 MPF は行い、プロジェクトの種類の詳細を実装することに専念する多くの Visual Studio が提供するため、プロジェクトの型を受け取るインターフェイスを実装します。  
  
## <a name="using-the-mpf-project-source-code"></a>プロジェクトの MPF ソース コードを使用します。  
 管理されているパッケージのプロジェクトのフレームワーク (MPFProj) を作成して、新しいプロジェクト システムを管理するためのヘルパー クラスを提供します。 MPF の他のクラスとは異なり Visual Studio に付属するアセンブリにはプロジェクトのクラスが含まれません。 ソース コードとしてプロジェクトのクラスを提供する代わりに、 [2013 のプロジェクトの MPF](http://mpfproj12.codeplex.com)します。  
  
 VSPackage ソリューションには、このプロジェクトを追加するには、次の操作を行います。  
  
1.  MPFProj ファイルをダウンロードする*MPFProjectDir*します。  
  
2.  *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file、次のブロックを変更します。  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  VSPackage プロジェクトを作成します。  
  
2.  VSPackage プロジェクトをアンロードします。  
  
3.  もう一方の前に次のブロックを追加することで、VSPackage .csproj ファイルを編集`<Import>`ブロック。  
  
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
  
3.  VSPackage プロジェクトを再度開きます。 ProjectBase をという名前の新しいディレクトリが表示されます。  
  
4.  VSPackage プロジェクトに次の参照を追加します。  
  
     Microsoft.Build.Tasks.4.0  
  
5.  プロジェクトをビルドします。  
  
## <a name="hierarchy-classes"></a>クラスの階層  
 次の表は、プロジェクトの階層をサポートしている、MPFProj でクラスをまとめたものです。 詳細については、次を参照してください。[階層と選択](../../extensibility/internals/hierarchies-and-selection.md)します。  
  
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
 次の表は、ドキュメントの処理をサポートしている MPF でクラスを一覧表示します。 詳細については、次を参照してください。[開始タグとプロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)します。  
  
|クラス名|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>構成と出力クラス  
 次の表では、プロジェクトの種類のデバッグとリリースでは、プロジェクト出力のコレクションなどの複数の構成をサポートするのに便利な MPF のクラスを示します。 詳細については、次を参照してください。[構成オプションを管理する](../../extensibility/internals/managing-configuration-options.md)です。  
  
|クラス名|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>オートメーション サポート クラス  
 次の表は、プロジェクトの種類のユーザーがアドインを作成できるように自動化をサポートする MPF のクラスを示します。  
  
|クラス名|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>プロパティ クラス  
 次の表は、プロジェクトの種類に便利な MPF 内のクラスでは、ユーザーが参照およびプロパティ ブラウザーで変更できるプロパティを追加します。  
  
|クラス名|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
