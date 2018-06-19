---
title: Managed Package Framework を使用して、プロジェクトの種類 (c#) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 112988f28728d40509a3af0360246a6bb4caef1a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140204"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Managed Package Framework を使用して、プロジェクトの種類 (c#) を実装するには
Managed Package Framework (MPF) は、c# クラスを使用するか、独自のプロジェクトの種類を実装する継承を提供します。 MPF は、維持、プロジェクトの種類の詳細を実装することに専念する多くの Visual Studio でプロジェクトの種類を指定するインターフェイスを実装します。  
  
## <a name="using-the-mpf-project-source-code"></a>MPF プロジェクトのソース コードを使用します。  
 (MPFProj) のプロジェクト用 Managed Package Framework は、作成して、新しいプロジェクト システムを管理するためのヘルパー クラスを提供します。 MPF で他のクラスとは異なり、プロジェクトのクラスは Visual Studio に付属のアセンブリに含まれていません。 ソース コードとしてプロジェクト クラスを提供する代わりに、 [2013 のプロジェクトの MPF](http://mpfproj12.codeplex.com)です。  
  
 VSPackage ソリューションには、このプロジェクトを追加するには、次の操作を行います。  
  
1.  MPFProj ファイルをダウンロードする*MPFProjectDir*です。  
  
2.  *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file、次のブロックを変更します。  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  VSPackage プロジェクトを作成します。  
  
2.  VSPackage プロジェクトをアンロードします。  
  
3.  VSPackage .csproj ファイルを編集する前に、他の次のブロックを追加することによって`<Import>`ブロック。  
  
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
  
2.  VSPackage のソリューションを閉じてから開き。  
  
3.  VSPackage プロジェクトを再度開きます。 ProjectBase をという名前の新しいディレクトリが表示されます。  
  
4.  次の参照を VSPackage プロジェクトを追加します。  
  
     Microsoft.Build.Tasks.4.0  
  
5.  プロジェクトをビルドします。  
  
## <a name="hierarchy-classes"></a>クラスの階層  
 次の表は、プロジェクトの階層をサポートしている、MPFProj でクラスをまとめたものです。 詳細については、次を参照してください。[階層と選択](../../extensibility/internals/hierarchies-and-selection.md)です。  
  
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
 次の表は、ドキュメントの処理をサポートしている MPF でクラスを一覧表示します。 詳細については、次を参照してください。[開始タグとプロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)です。  
  
|クラス名|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>構成と出力クラス  
 次の表では、プロジェクトの種類のデバッグとリリースでは、プロジェクト出力のコレクションなどの複数の構成をサポートするのに便利な MPF クラスは、一覧表示します。 詳細については、次を参照してください。[構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)です。  
  
|クラス名|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>オートメーションのサポート クラス  
 次の表は、プロジェクトの種類のユーザーがアドインを作成できるように、オートメーションをサポートしている MPF でクラスを一覧表示します。  
  
|クラス名|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>プロパティ クラス  
 次の表は、プロジェクトの種類に便利な MPF クラスでは、ユーザーが参照およびプロパティ ブラウザーで変更できるプロパティを追加します。  
  
|クラス名|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|