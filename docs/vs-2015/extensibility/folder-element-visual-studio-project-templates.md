---
title: Folder 要素 (Visual Studio プロジェクト テンプレート) |Microsoft Docs
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
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 486448ec92ef05890c95ec5277e5b5b99e976231
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236159"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

プロジェクトに追加されるフォルダーを指定します。  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Project>  
 \<フォルダー >  
  
## <a name="syntax"></a>構文  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須の属性です。<br /><br /> プロジェクト フォルダーの名前。|  
|`TargetFolderName`|省略可能な属性です。<br /><br /> テンプレートからプロジェクトが作成されるフォルダーを指定する名前を指定します。 この属性は、パラメーター置換を使用して、フォルダー名を作成するのに役立ちます。 または .zip ファイルで直接、国際対応の文字列でフォルダーの名前は使用できません。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|`Folder`|プロジェクトに追加するフォルダーを指定します。 `Folder` 要素が子を含めることができます`Folder`要素。|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|プロジェクトに追加するファイルを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[プロジェクト](../extensibility/project-element-visual-studio-templates.md)|省略可能な子要素の[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)します。|  
  
## <a name="remarks"></a>Remarks  
 `Folder` 省略可能な子の`Project`します。  
  
 テンプレート内のフォルダーにプロジェクト項目を整理するのにには、次の方法のいずれかを使用できます。  
  
-   テンプレートの .zip ファイルとフォルダーを含めるしでファイルへのパスを指定することで、.vstemplate ファイルでプロジェクトに追加、`ProjectItem`なしで、要素`Folder`要素。 これは、推奨される方法です。 例えば:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   テンプレートの .zip ファイルとフォルダーを含めるし、.vstemplate ファイルでプロジェクトに追加`Folder`要素。 例えば:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   テンプレートの .zip ファイル内のフォルダーを含めないでくださいを使用してフォルダーを追加、`TargetFileName`の属性、`ProjectItem`要素。 例えば:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>例  
 次の例のためのプロジェクト テンプレート メタデータを[!INCLUDE[csprcs](../includes/csprcs-md.md)]Windows アプリケーション。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [ProjectItem 要素 (Visual Studio 項目テンプレート)](../extensibility/projectitem-element-visual-studio-item-templates.md)

