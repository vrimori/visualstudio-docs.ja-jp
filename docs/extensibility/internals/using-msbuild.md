---
title: "MSBuild の使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild を使用してコンパイルする VSPackages"
  - "MSBuild の機能拡張"
  - "MSBuild を使用してコンパイルするパッケージ"
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# MSBuild の使用
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

MSBuild では、ビルド、ビルド タスク、および構成をビルドするプロジェクト アイテムを完全に記述するプロジェクト ファイルを作成するために適切に定義された、拡張性の高い XML 形式が用意されています。  
  
 MSBuild に基づいて言語プロジェクト システムのエンド ツー エンド サンプルでは、\[IronPython サンプルの詳細情報を参照してください、[VSSDK のサンプル](../../misc/vssdk-samples.md)です。  
  
## 一般的な MSBuild に関する考慮事項  
 MSBuild プロジェクト ファイル、たとえば、 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj と [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vbproj ファイルには、ビルド時に使用されるが、デザイン時に使用されるデータも含めることができますデータが含まれています。 含む MSBuild プリミティブを使用してビルド時のデータを格納 [Item Element \(MSBuild\)](../../msbuild/item-element-msbuild.md) と [Property Element \(MSBuild\)](../../msbuild/property-element-msbuild.md)です。 プロジェクトの種類および関連するプロジェクトのサブタイプに固有のデータが、デザイン時のデータは、用に予約自由形式の XML に格納されます。  
  
 MSBuild では、構成オブジェクトのネイティブ サポートしていないは、条件付き属性の構成に固有のデータを指定するため実現します。 例:  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 条件付き属性の詳細については、次を参照してください。 [Conditional Constructs](../../msbuild/msbuild-conditional-constructs.md)します。  
  
### MSBuild を拡張する、プロジェクトの種類  
 MSBuild は、インターフェイスの Api がの将来のバージョンで変更される可能性が [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 そのため、変更からシールドを提供するために、マネージ パッケージ フレームワーク \(MPF\) クラスを使用することをお勧めします。  
  
 管理されているパッケージのプロジェクトのフレームワーク \(MPFProj\) を作成して、新しいプロジェクト システムを管理するためのヘルパー クラスを提供します。 コードとコンパイル」の手順にソースを検索できる [Visual Studio 2013 のプロジェクトの MPF](http://mpfproj12.codeplex.com/)します。  
  
 プロジェクト固有の MPF クラスは次のとおりです。  
  
|クラス|実装|  
|---------|--------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` クラスは、MSBuild アイテム用のラッパーです。  
  
#### 単一ファイル ジェネレーター vs します。MSBuild タスク  
 単一ファイル ジェネレーターは、デザイン時のみにアクセスできるが、MSBuild タスクは、デザイン時およびビルド時に使用できます。 最大限の柔軟性、したがってを変換し、コードを生成する MSBuild タスクを使用します。 詳細については、「[カスタム ツール](../../extensibility/internals/custom-tools.md)」を参照してください。  
  
## 参照  
 [MSBuild Reference](../../msbuild/msbuild-reference.md)   
 [MSBuild](http://msdn.microsoft.com/ja-jp/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [カスタム ツール](../../extensibility/internals/custom-tools.md)