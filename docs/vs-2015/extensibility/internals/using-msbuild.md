---
title: MSBuild の使用 |Microsoft Docs
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
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8b776823c78835ad687a110c1fcc0ba1382bead
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535394"
---
# <a name="using-msbuild"></a>MSBuild の使用
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[を使用して MSBuild](https://docs.microsoft.com/visualstudio/extensibility/internals/using-msbuild)します。  
  
MSBuild では、ビルド、ビルド タスク、および構成をビルドするプロジェクト アイテムを完全に記述するプロジェクト ファイルを作成するために適切に定義された、拡張性の高い XML 形式を提供します。  
  
 MSBuild に基づく言語プロジェクト システムのエンド ツー エンド サンプルで IronPython サンプルの詳細情報を参照してください、[VSSDK のサンプル](../../misc/vssdk-samples.md)します。  
  
## <a name="general-msbuild-considerations"></a>MSBuild の一般的な考慮事項  
 MSBuild プロジェクト ファイル、たとえば、 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] .csproj および[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]、.vbproj ファイルには、ビルド時に使用されますが、デザイン時に使用されるデータを含めることができますもデータが含まれています。 などの MSBuild のプリミティブを使用して、ビルド時のデータが格納された[Item 要素 (MSBuild)](../../msbuild/item-element-msbuild.md)と[Property 要素 (MSBuild)](../../msbuild/property-element-msbuild.md)します。 プロジェクトの種類との関連プロジェクト サブタイプに固有のデータである、デザイン時のデータは、自由形式の XML 用に予約に格納されます。  
  
 MSBuild では、構成オブジェクトのネイティブ サポートはありませんが、構成に固有のデータを指定するための条件付き属性は提供します。 例えば:  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 条件付き属性の詳細については、次を参照してください。[条件構造](../../msbuild/msbuild-conditional-constructs.md)します。  
  
### <a name="extending-msbuild-for-your-project-type"></a>種類のプロジェクトの MSBuild の拡張  
 MSBuild のインターフェイスと Api は、の将来のバージョンで変更される可能性は[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 そのため、変更からシールドを提供するために、マネージ パッケージ フレームワーク (MPF) クラスを使用することをお勧めします。  
  
 Managed Package Framework (MPFProj) プロジェクトを作成して、新しいプロジェクト システムを管理するためのヘルパー クラスを提供します。 コードとコンパイル」の手順に従って、ソースを検索できる[- Visual Studio 2013 のプロジェクトの MPF](http://mpfproj12.codeplex.com/)します。  
  
 プロジェクトに固有の MPF クラスは次のとおりです。  
  
|クラス|実装|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` クラスは、MSBuild 項目用のラッパーです。  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>単一ファイル ジェネレーターの vs します。MSBuild タスク  
 単一ファイル ジェネレーターは、デザイン時のみにアクセスできるが、デザイン時およびビルド時に MSBuild タスクを使用できます。 最大限の柔軟性の変換し、コードを生成する MSBuild タスクを使用してそのため。 詳細については、次を参照してください。[カスタム ツール](../../extensibility/internals/custom-tools.md)します。  
  
## <a name="see-also"></a>関連項目  
 [MSBuild リファレンス](../../msbuild/msbuild-reference.md)   
 [MSBuild](http://msdn.microsoft.com/en-us/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [カスタム ツール](../../extensibility/internals/custom-tools.md)

