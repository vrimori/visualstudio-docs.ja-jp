---
title: MSBuild の使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4115d6f1b368734631acf3ee4395d71dbe418c07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-msbuild"></a>MSBuild の使用
MSBuild では、プロジェクト項目を作成、ビルド タスク、およびビルド構成を完全に記述するプロジェクト ファイルを作成するために適切に定義された、拡張可能な XML 形式を指定します。  
  
## <a name="general-msbuild-considerations"></a>一般的な MSBuild に関する考慮事項  
 MSBuild プロジェクト ファイル、たとえば、 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj および[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)].vbproj ファイル、含めるデータがあるがビルド時に使用しても、デザイン時に使用されるデータを含めることができます。 MSBuild プリミティブなどを使用してビルド時のデータが格納された[Item 要素 (MSBuild)](../../msbuild/item-element-msbuild.md)と[Property 要素 (MSBuild)](../../msbuild/property-element-msbuild.md)です。 プロジェクトの種類との関連プロジェクト サブタイプに固有のデータである、デザイン時のデータは、用に予約自由形式の XML に格納されます。  
  
 MSBuild は構成オブジェクトのネイティブ サポートはありませんが、構成に固有のデータを指定するための条件付き属性は提供します。 例えば:  
  
```xml  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 条件付き属性の詳細については、次を参照してください。[条件付き構築](../../msbuild/msbuild-conditional-constructs.md)です。  
  
### <a name="extending-msbuild-for-your-project-type"></a>MSBuild のプロジェクトの種類の拡張  
 MSBuild は、インターフェイスの Api が将来のバージョンの変更の対象[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 そのため、変更からシールドを提供するために、マネージ パッケージ フレームワーク (MPF) クラスを使用することをお勧めします。  
  
 (MPFProj) のプロジェクト用 Managed Package Framework は、作成して、新しいプロジェクト システムを管理するためのヘルパー クラスを提供します。 コードとコンパイル」の手順にソースを検索できる[プロジェクトの Visual Studio 2013 の MPF](http://mpfproj12.codeplex.com/)です。  
  
 プロジェクト固有の MPF クラスは次のとおりです。  
  
|クラス|実装|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` クラスは、MSBuild 項目用のラッパーです。  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>単一ファイル ジェネレーター vs です。MSBuild タスク  
 単一ファイル ジェネレーターは、デザイン時にのみ、アクセスできるが、デザイン時およびビルド時に MSBuild タスクを使用できます。 柔軟性を最大限に高めるそのため、MSBuild タスクを使用して変換し、コードを生成します。 詳細については、次を参照してください。[カスタム ツール](../../extensibility/internals/custom-tools.md)です。  
  
## <a name="see-also"></a>関連項目  
 [MSBuild リファレンス](../../msbuild/msbuild-reference.md)   
 [MSBuild](../../msbuild/msbuild.md)   
 [カスタム ツール](../../extensibility/internals/custom-tools.md)