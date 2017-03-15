---
title: "ProjectSubType 要素 (Visual Studio テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType"
helpviewer_keywords: 
  - "<ProjectSubType> 要素 [Visual Studio テンプレート]"
  - "ProjectSubType 要素 [Visual Studio テンプレート]"
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# ProjectSubType 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`ProjectType` 要素で指定した値のサブカテゴリにテンプレートを分類します。  
  
## 構文  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
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
  
 テキスト値には、テンプレートのサブカテゴリを指定します。  
  
## 解説  
 `ProjectSubType` は、`TemplateData` の子要素で、省略可能な要素です。  
  
 `ProjectSubType` 要素で、[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) 要素のサブカテゴリを作成できます。  この要素には次のような値が含まれます。  
  
-   `SmartDevice-NETCFv1`: テンプレートが [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] バージョン 1.0 を対象とするように指定します。  
  
-   `SmartDevice-NETCFv2`: テンプレートが [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] バージョン 2.0 を対象とするように指定します。  
  
 テンプレートに `Web` の値を持った `ProjectType` 要素がある場合、`ProjectSubType` 要素は、テンプレートのプログラミング言語を指定します。  この要素には、次の値を指定できます。  
  
-   `CSharp`: テンプレートが [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] の Web プロジェクトまたは Web アイテムを作成するよう指定します。  
  
-   `VisualBasic`: テンプレートが [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の Web プロジェクトまたは Web アイテムを作成するよう指定します。  
  
## 使用例  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] デバイス アプリケーションでのプロジェクト テンプレートのメタデータの例を次に示します。このデバイスアプリケーションは、[!INCLUDE[Compact](../extensibility/includes/compact_md.md)] バージョン 2.0 を対象としています。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
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
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [ProjectType 要素 \(Visual Studio テンプレート\)](../extensibility/projecttype-element-visual-studio-templates.md)