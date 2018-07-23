---
title: BuildProjectOnload 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e5cbcc06fcc7a936918de8b1a9d4c44d9938d94
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154159"
---
# <a name="buildprojectonload-element-visual-studio-templates"></a>BuildProjectOnload 要素 (Visual Studio テンプレート)
作成して、ソリューションに追加するときは、新しいプロジェクトのみをビルドします。 ソリューション全体はビルドされません。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<BuildProjectOnLoad>  
  
## <a name="syntax"></a>構文  
  
```vb  
<BuildProjectOnLoad> true/false </BuildOnLoad>  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`TemplateData`|テンプレートを分類し、両方での表示方法を定義、**新しいプロジェクト**と**新しい項目の追加** ダイアログ ボックス。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 テキストがいずれかにする必要があります`true`または`false`をテンプレートから作成時に新しいプロジェクトのみをビルドするかどうかを示します。  
  
## <a name="remarks"></a>Remarks  
 `BuildProjectOnLoad` は、省略可能な要素です。 既定値は `false` です。  
  
## <a name="example"></a>例  
 次の例では、Visual c# テンプレートのメタデータを示しています。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <BuildProjectOnload>true</BuildProjectOnLoad>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトと項目テンプレートを作成します。](../ide/creating-project-and-item-templates.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)