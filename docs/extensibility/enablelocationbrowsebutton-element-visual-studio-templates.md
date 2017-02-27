---
title: "EnableLocationBrowseButton 要素 (Visual Studio テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton"
helpviewer_keywords: 
  - "EnableLocationBrowseButton [Visual Studio プロジェクト テンプレート]"
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# EnableLocationBrowseButton 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**\[新しいプロジェクト\]** ダイアログ ボックスの **\[参照\]** ボタンを使用できるようにするかどうかを指定します。このボタンが使用できると、新規プロジェクトを保存するための既定ディレクトリを簡単に変更できます。  
  
## 構文  
  
```  
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素。<br /><br /> テンプレートをカテゴリに分類し、**\[新しいプロジェクト\]** ダイアログ ボックス、または **\[新しい項目の追加\]** ダイアログ ボックスでどのように表示させるかを定義します。|  
  
## テキスト値  
 テキスト値が必要です。  
  
 `true` または `false` のいずれかを設定する必要があります。これは、**\[新しいプロジェクト\]** ダイアログ ボックスの **\[参照\]** ボタンを表示するかどうかを示します。  
  
## 解説  
 `EnableLocationBrowseButton` は、省略可能な要素です。  既定値は `true` です。これにより、**\[新しいプロジェクト\]** ダイアログ ボックスの **\[参照\]** ボタンが表示されます。  
  
 **\[新しいプロジェクト\]** ダイアログ ボックスの **\[場所\]** ボックスで、新規プロジェクトを保存するディレクトリを指定します。  **\[参照\]** ボタンで、**\[プロジェクトの場所\]** ダイアログ ボックスを表示してこのディレクトリを変更できます。これにより、自分のコンピューターから利用できる別のディレクトリへ簡単に移動でき、そのディレクトリを新規プロジェクトの保存先として選択できます。  
  
## 使用例  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows アプリケーションでのメタデータの例を次に示します。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>  
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