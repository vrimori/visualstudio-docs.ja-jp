---
title: "NumberOfParentCategoriesToRollUp (Visual Studio テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp"
helpviewer_keywords: 
  - "<NumberOfParentCategoriesToRollUp> 要素 [Visual Studio テンプレート]"
  - "NumberOfParentCategoriesToRollUp 要素 [Visual Studio テンプレート]"
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# NumberOfParentCategoriesToRollUp (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**\[新しいプロジェクト\]** ダイアログ ボックスに表示されるテンプレートの親カテゴリの数を指定します。  
  
## 構文  
  
```  
<NumberOfParentCategoriesToRollUp>  
    1  
</NumberOfParentCategoriesToRollUp>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|テンプレートをカテゴリに分類し、**\[新しいプロジェクト\]** ダイアログ ボックス、または **\[新しい項目の追加\]** ダイアログ ボックスでどのように表示させるかを定義します。|  
  
## テキスト値  
 `integer` 値は必須です。  
  
 この値は、**\[新しいプロジェクト\]** ダイアログ ボックスに表示されるテンプレートの親カテゴリの数を指定します。  
  
## 解説  
 `NumberOfParentCategoriesToRollUp` は、省略可能な要素です。  
  
## 使用例  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows アプリケーションでのメタデータの例を次に示します。  このメタデータを含むテンプレートが最上位の [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ノードより 2 つ下のフォルダーに配置されている場合、テンプレートは、**\[新しいプロジェクト\]** ダイアログ ボックスの最上位のノードに表示されます。  `NumberOfParentCategoriesToRollUp` が設定されていない場合、テンプレートは物理的に配置されているノードに表示されます。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>  
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