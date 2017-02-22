---
title: "ProjectCollection 要素 (Visual Studio Templates) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection"
helpviewer_keywords: 
  - "<ProjectCollection> 要素 [Visual Studio テンプレート]"
  - "ProjectCollection 要素 [Visual Studio テンプレート]"
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# ProjectCollection 要素 (Visual Studio Templates)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

複数プロジェクトのテンプレートの構成と内容を指定します。  
  
## 構文  
  
```  
<ProjectCollection>  
    <ProjectTemplateLink> ... </ProjectTemplateLink>  
    <SolutionFolder> ... </SolutionFolder>  
</ProjectCollection>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 複数プロジェクトのテンプレートのプロジェクトを指定します。|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 複数プロジェクトのテンプレートをグループ化します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必須の要素。<br /><br /> テンプレートの内容を指定します。|  
  
## 解説  
 複数プロジェクトのテンプレートは、2 つ以上のプロジェクトのコンテナーとして機能します。  `ProjectCollection` 要素は、テンプレートに含めるプロジェクトを指定するために使用します。  複数プロジェクトのテンプレートの詳細については、「[方法 : 複数プロジェクトのテンプレートを作成する](../ide/how-to-create-multi-project-templates.md)」を参照してください。  
  
## 使用例  
 簡単なマルチプロジェクトのルート .vstemplate ファイルの例を次に示します。  この例では、テンプレートには `My Windows Application` と `My Class Library` の 2 つのプロジェクトが含まれています。  `ProjectTemplateLink` 要素の `ProjectName` 属性は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がこのプロジェクトに割り当てる名前を設定します。  `ProjectName` 属性が存在しない場合、.vstemplate ファイルの名前がプロジェクト名として使用されます。  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [方法 : 複数プロジェクトのテンプレートを作成する](../ide/how-to-create-multi-project-templates.md)