---
title: "プロジェクトの要素 (Visual Studio テンプレート) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f2995f6486ebb8d3e305c70c03fb543fab04b67a
ms.lasthandoff: 02/22/2017

---
# <a name="project-element-visual-studio-templates"></a>Project 要素 (Visual Studio テンプレート)
ファイルまたはプロジェクトに追加するディレクトリを指定します。  
  
 \<VSTemplate >  
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
|`File`|必須の属性です。<br /><br /> テンプレートの .zip ファイルで、プロジェクト ファイルの名前を指定します。|  
|`ReplaceParameters`|省略可能な属性です。<br /><br /> プロジェクト ファイルが、テンプレートからプロジェクトが作成されるときに置き換える必要があるパラメーターの値を持つかどうかを指定するブール値。 既定値は `false` です。|  
|`TargetFileName`|省略可能な属性です。<br /><br /> プロジェクトが、テンプレートから作成されたときに、プロジェクト ファイルの名前を指定します。|  
|`IgnoreProjectParameter`|省略可能な属性です。<br /><br /> 現在のソリューションにプロジェクトを追加するかどうかを指定します。 場合は、カスタム パラメーターの値"$*myCustomParameter*$"が存在するプロジェクトの作成が現在開いているソリューションの一部として追加しないと、パラメーター置換ファイル内です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[フォルダー](../extensibility/folder-element-visual-studio-project-templates.md)|省略可能な要素です。<br /><br /> プロジェクトに追加するフォルダーを指定します。|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|省略可能な要素です。<br /><br /> プロジェクトに追加するファイルを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必須の要素です。|  
  
## <a name="remarks"></a>コメント  
 `Project` は、`TemplateContent` の子要素で、省略可能な要素です。  
  
 `Project`要素は、プロジェクトを指定するために使用および、そのため、プロジェクト テンプレートで有効なだけです。  
  
 `Project`要素があることができます[フォルダー](../extensibility/folder-element-visual-studio-project-templates.md)子要素または[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)子要素が、両方の混在させないように`Folder`と`ProjectItem`子要素です。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ユーザーが入力した名前に基づいて、プロジェクト ファイル名が自動的に変更、**新しいプロジェクト** ダイアログ ボックス。 使用して、`TargetFileName`属性の場合は、テンプレートを使用して作成されたプロジェクト ファイルの別のファイル名を指定します。  
  
## <a name="example"></a>例  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] アプリケーションでのプロジェクト テンプレートのメタデータの例を次に示します。  
  
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
 [プロジェクトおよび項目テンプレートを作成します。](../ide/creating-project-and-item-templates.md)   
 [ProjectItem 要素 (Visual Studio プロジェクト テンプレート)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder 要素 (Visual Studio プロジェクト テンプレート)](../extensibility/folder-element-visual-studio-project-templates.md)
