---
title: '方法: 複数のプロジェクト ファイルで同じターゲットを使用する | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41c1ed02a32136d6c80e24f0644e0fab660e8ed0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31571813"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>方法 : 複数のプロジェクト ファイルで同じターゲットを使用する
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルを作成した経験があれば、同じタスクとターゲットを別のプロジェクト ファイルで使用する必要があることにお気付きでしょう。 すべてのプロジェクト ファイルにそれらのタスクやターゲットの完全な説明を追加する代わりに、個別のプロジェクト ファイルにターゲットを保存し、そのプロジェクトをそのターゲットを必要とする他のプロジェクトにインポートできます。  
  
## <a name="using-the-import-element"></a>Import 要素の使用  
 `Import` 要素は、あるプロジェクト ファイルを別のプロジェクト ファイルに挿入するために使用されます。 インポートされるプロジェクト ファイルは有効な [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクト ファイルでなければならず、整形式の XML が含まれている必要があります。 `Project` 属性は、インポートされたプロジェクト ファイルのパスを指定します。 `Import` 要素に関する詳細については、「[Import 要素 (MSBuild)](../msbuild/import-element-msbuild.md)」を参照してください。  
  
#### <a name="to-import-a-project"></a>プロジェクトをインポートするには  
  
1.  インポートを行うプロジェクトのファイルで、インポートされるプロジェクトのプロパティとアイテムを対象に、パラメーターとして使用されるすべてのプロパティとアイテムを定義します。  
  
2.  `Import` 要素を使用し、プロジェクトをインポートします。 例:  
  
     `<Import Project="MyCommon.targets"/>`  
  
3.  `Import` 要素に続き、インポートされるプロジェクトのプロパティとアイテムの既定の定義を無視するすべてのプロパティとアイテムを定義します。  
  
## <a name="order-of-evaluation"></a>評価の順序  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] が `Import` 要素に到達すると、インポートされるプロパティとアイテムは、`Import` 要素の場所で、インポートを行うプロジェクトに効果的に挿入されます。 そのため、`Import` 要素の場所は、プロパティとアイテムの値に影響を与えます。 インポートされるプロジェクトにより設定されるプロパティとアイテムとインポートされるプロジェクトで使用されるプロパティとアイテムを理解することが重要です。  
  
 プロジェクトをビルドするとき、すべてのプロパティが最初に評価され、続いてアイテムが評価されます。 たとえば、次の XML では、インポートされるプロジェクトファイル MyCommon.targets が定義されます。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyCommon</Name>  
    </PropertyGroup>  
  
    <Target Name="Go">  
        <Message Text="Name=$(Name)"/>  
    </Target>  
</Project>  
```  
  
 次の XML は MyApp.proj を定義します。MyApp.proj は MyCommon.targets をインポートします。  
  
```xml  
<Project  
    DefaultTargets="Go"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyApp</Name>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
 プロジェクトをビルドするとき、次のメッセージが表示されます。  
  
 `Name="MyCommon"`  
  
 プロジェクトはプロパティ `Name` が MyApp.proj で定義された後にインポートされるため、MyCommon.targets の `Name` の定義により MyApp.proj の定義が無視されます。 プロパティ Name が定義される前にプロジェクトがインポートされた場合、ビルドは次のメッセージを表示します。  
  
 `Name="MyApp"`  
  
#### <a name="use-the-following-approach-when-importing-projects"></a>プロジェクトのインポート時に次のアプローチを使用する  
  
1.  プロジェクトのファイルで、インポートされるプロジェクトのプロパティとアイテムを対象に、パラメーターとして使用されるすべてのプロパティとアイテムを定義します。  
  
2.  プロジェクトをインポートします。  
  
3.  プロジェクト ファイルで、インポートされるプロジェクトのプロパティとアイテムの既定の定義を無視するすべてのプロパティとアイテムを定義します。  
  
## <a name="example"></a>例  
 次のコード サンプルは、2 つ目のコード サンプルがインポートする MyCommon.targets ファイルを示します。 .targets ファイルは、インポートを行うプロジェクトからのプロパティを評価してビルドを構成します。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>  
        <appname>$(MSBuildProjectName)</appname>  
    <PropertyGroup>  
    <Target Name="Build">  
        <Csc Sources="hello.cs"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>例  
 次のコード サンプルは、MyCommon.targets ファイルをインポートします。  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor>RETAIL</Flavor>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
## <a name="see-also"></a>参照  
 [Import 要素 (MSBuild)](../msbuild/import-element-msbuild.md)   
 [ターゲット](../msbuild/msbuild-targets.md)