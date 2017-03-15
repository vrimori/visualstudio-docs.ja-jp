---
title: "Folder 要素 (Visual Studio テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Folder"
helpviewer_keywords: 
  - "Folder 要素 [Visual Studio プロジェクト テンプレート]"
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Folder 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロジェクトに追加するフォルダーを指定します。  
  
## 構文  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`Name`|必須の属性です。<br /><br /> プロジェクト フォルダーの名前です。|  
|`TargetFolderName`|省略可能な属性です。<br /><br /> プロジェクトがテンプレートから作成されるときのフォルダー名を指定します。  この属性は、フォルダー名を作成するためにパラメーター置換を使用したり、.zip ファイルでは直接使用できない各国対応の文字列を含むフォルダーの名前を変更したりする場合に便利です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|`Folder`|プロジェクトに追加するフォルダーを指定します。  `Folder` 要素は、子の `Folder` 要素を持つことができます。|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|プロジェクトに追加するファイルを指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md) の省略可能な子要素です。|  
  
## 解説  
 `Folder` は `Project` の省略可能な子要素です。  
  
 テンプレート内のフォルダーにあるプロジェクト アイテムは、次のいずれかの方法で整理します。  
  
-   テンプレート .zip ファイルにフォルダーを含めます。そして `Folder` 要素を持たない `ProjectItem` 要素に .vstemplate ファイルへのパスを指定して、.vstemplate ファイル内のプロジェクトにフォルダーを追加します。  この方法は推奨されている方法です。  次に例を示します。  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   テンプレート .zip ファイルにフォルダーを含めます。そして `Folder` 要素を使って .vstemplate ファイル内のプロジェクトにフォルダーを追加します。  次に例を示します。  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   テンプレート .zip ファイルにフォルダーを含めないで、`ProjectItem` 要素の `TargetFileName` 属性を使用してフォルダーを追加します。  次に例を示します。  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## 使用例  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows アプリケーションでのプロジェクト テンプレートのメタデータの例を次に示します。  
  
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
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [ProjectItem 要素 \(Visual Studio 項目テンプレート\)](../extensibility/projectitem-element-visual-studio-item-templates.md)