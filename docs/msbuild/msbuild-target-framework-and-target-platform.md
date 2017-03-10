---
title: "MSBuild ターゲット フレームワークおよびターゲット プラットフォーム | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: f91e102854a83cc70e7b7f4adbc2cd2afb727b07
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild ターゲット フレームワークおよびターゲット プラットフォーム
プロジェクトは*ターゲット フレームワーク*とターゲット プラットフォームで動作するようにビルドできます。ターゲット フレームワークとは .NET Framework の特定のバージョンを表し、*ターゲット プラットフォーム*とは特定のソフトウェア アーキテクチャを表します。  たとえば、802x86 プロセッサ ファミリ ("x86") と互換性のある 32 ビット プラットフォーム上の .NET Framework 2.0 で動作するアプリケーションを対象とすることができます。 ターゲット フレームワークとターゲット プラットフォームの組み合わせは*ターゲット コンテキスト*と呼ばれます。  
  
## <a name="target-framework-and-profile"></a>ターゲット フレームワークとプロファイル  
 ターゲット フレームワークとは、ビルドするプロジェクトの実行対象とする [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の特定のバージョンを意味します。 ターゲット フレームワークの仕様は必須です。これは、ターゲット フレームワークの仕様によって、そのフレームワークのバージョン専用のコンパイラ機能とアセンブリ参照が利用可能になるためです。  
  
 現在、.NET Framework については次のバージョンを使用できます。  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 (Visual Studio 2005 に付属しています)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.0 ([!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] に付属しています)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 ([!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] に付属しています)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4 (Visual Studio 2005 に付属しています)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5 ([!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] に付属しています)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5.1 ([!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] に付属しています)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]4.5.2  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6 ([!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)] に付属しています)  
  
 .NET Framework の各バージョンでは、参照できるアセンブリの一覧がそれぞれ異なっています。 たとえば、WPF (Windows Presentation Foundation) アプリケーションをビルドするには、プロジェクトが .NET Framework のバージョン 3.0 以上 を対象としている必要があります。  
  
 ターゲット フレームワークは、プロジェクト ファイルの `TargetFrameworkVersion` プロパティで指定されます。 プロジェクトのターゲット フレームワークを変更するには、Visual Studio 統合開発環境 (IDE) でプロジェクトのプロパティ ページを使用します。 詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../ide/how-to-target-a-version-of-the-dotnet-framework.md)」を参照してください。 `TargetFrameworkVersion` に使用できる値は、`v2.0`、`v3.0`、`v3.5`、`v4.0`、`v4.5`、`v4.5.1`、`v4.5.2`、`v4.6` です。  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 *目標一覧表*はターゲット フレームワークのサブセットです。 たとえば、.NET Framework 4 Client Profile には、MSBuild アセンブリへの参照が含まれていません。  
  
 ターゲット プロファイルは、プロジェクト ファイルの `TargetFrameworkProfile` プロパティで指定されます。 目標一覧表を変更するには、IDE でプロジェクトのプロパティ ページにあるターゲット フレームワークのコントロールを使用します。 詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../ide/how-to-target-a-version-of-the-dotnet-framework.md)」を参照してください。  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>ターゲット プラットフォーム  
 *プラットフォーム*は、特定のランタイム環境を定義するハードウェアとソフトウェアの組み合わせです。 次に例を示します。  
  
-   `x86` は、Intel 80x86 プロセッサまたはそれに相当するプロセッサで実行されている 32 ビット Windows オペレーティング システムを示しています。  
  
-   `Xbox` は、Microsoft Xbox 360 プラットフォームを示しています。  
  
 *ターゲット プラットフォーム*は、ビルドするプロジェクトの実行対象となる特定のプラットフォームです。 ターゲット プラットフォームは、プロジェクト ファイルの `Platform` ビルド プロパティで指定されます。 ターゲット プラットフォームを変更するには、IDE でプロジェクトのプロパティ ページまたは **[構成マネージャー]** を使用します。  
  
```xml  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 *ターゲット構成*はターゲット プラットフォームのサブセットです。 たとえば、`x86``Debug` 構成には、ほとんどのコード最適化が含まれていません。 ターゲット構成は、プロジェクト ファイルの `Configuration` ビルド プロパティで指定されます。 ターゲット構成を変更するには、プロジェクトのプロパティ ページまたは **[構成マネージャー]** を使用します。  
  
```xml  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>関連項目  
 [マルチ ターゲット](../msbuild/msbuild-multitargeting-overview.md)
