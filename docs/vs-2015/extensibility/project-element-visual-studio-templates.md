---
title: Project 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 07700501ae2a76337fed499aeb0a66b8b19dbeba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741127"
---
# <a name="project-element-visual-studio-templates"></a>Project 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ファイルまたはプロジェクトに追加するディレクトリを指定します。  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Project>  
  
## <a name="syntax"></a>構文  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`File`|必須の属性です。<br /><br /> テンプレートの .zip ファイルでは、プロジェクト ファイルの名前を指定します。|  
|`ReplaceParameters`|省略可能な属性です。<br /><br /> プロジェクト ファイルが、テンプレートからプロジェクトが作成されるときに置き換える必要があるパラメーター値を持つかどうかを指定するブール値。 既定値は `false`にする必要があります。|  
|`TargetFileName`|省略可能な属性です。<br /><br /> テンプレートからプロジェクトを作成するときは、プロジェクト ファイルの名前を指定します。|  
|`IgnoreProjectParameter`|省略可能な属性です。<br /><br /> 現在のソリューションにプロジェクトを追加するかどうかを指定します。 場合、カスタム パラメーターの値"$*myCustomParameter*$"が存在するプロジェクトの作成が現在開いているソリューションの一部として追加していない、パラメーター置換ファイルでします。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[フォルダー](../extensibility/folder-element-visual-studio-project-templates.md)|省略可能な要素です。<br /><br /> プロジェクトに追加するフォルダーを指定します。|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|省略可能な要素です。<br /><br /> プロジェクトに追加するファイルを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必須の要素です。|  
  
## <a name="remarks"></a>Remarks  
 `Project` は、`TemplateContent` の子要素で、省略可能な要素です。  
  
 `Project`要素は、プロジェクトを指定するために使用であるため、プロジェクト テンプレートでは有効で、のみです。  
  
 `Project` 要素が[フォルダー](../extensibility/folder-element-visual-studio-project-templates.md)子要素または[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) 、子要素が、両方の組み合わせではない`Folder`と`ProjectItem`子要素。  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ユーザーが入力した名前に基づいて、プロジェクト ファイル名を自動的に変更されます、**新しいプロジェクト** ダイアログ ボックス。 使用して、`TargetFileName`属性のテンプレートを使用して作成されるプロジェクト ファイルの代替ファイル名を指定する場合。  
  
## <a name="example"></a>例  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] アプリケーションでのプロジェクト テンプレートのメタデータの例を次に示します。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
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
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [ProjectItem 要素 (Visual Studio プロジェクト テンプレート)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder 要素 (Visual Studio プロジェクト テンプレート)](../extensibility/folder-element-visual-studio-project-templates.md)

