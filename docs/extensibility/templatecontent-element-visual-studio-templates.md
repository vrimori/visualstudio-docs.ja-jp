---
title: "TemplateContent 要素 (Visual Studio テンプレート) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent"
helpviewer_keywords: 
  - "TemplateContent 要素 [Visual Studio プロジェクト テンプレート]"
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# TemplateContent 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テンプレートの内容を指定します。  
  
## 構文  
  
```  
<TemplateContent>  
    ...  
</TemplateContent>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|テンプレートからプロジェクトを作成するときにソリューションをビルドするかどうかを指定します。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 複数プロジェクトのテンプレートの構成と内容を指定します。|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> プロジェクトに追加するファイルやディレクトリを指定します。|  
|[参照](../extensibility/references-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 項目テンプレートに必要なアセンブリ参照を指定します。|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|省略可能な要素です。<br /><br /> テンプレートに含まれているファイルを指定します。|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> テンプレートからプロジェクトまたはアイテムを作成するときに使用するカスタム パラメーターを指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必須の要素。<br /><br /> プロジェクト テンプレート、項目テンプレート、またはスタート キットのメタデータすべてを含みます。|  
  
## 解説  
 `TemplateContent` は必須の要素です。  
  
## 使用例  
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
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)