---
title: "WizardData 要素 (Visual Studio テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#WizardData"
helpviewer_keywords: 
  - "<WizardData> 要素 [Visual Studio テンプレート]"
  - "WizardData 要素 [Visual Studio テンプレート]"
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# WizardData 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

カスタムの XML を指定します。  
  
## 構文  
  
```  
<WizardData>  
    <!-- XML to pass to the custom wizard extension -->  
    ...  
</WizardData>  
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必須の要素。<br /><br /> プロジェクト テンプレート、項目テンプレート、またはスタート キットのメタデータすべてを含みます。|  
  
## テキスト値  
 テキスト値は省略可能です。  
  
 [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md) 要素で指定されたカスタム ウィザード拡張に渡すためのカスタム XML を指定します。  
  
## 解説  
 この要素には、任意の XML を指定できます。  XML はカスタム ウィザード拡張にパラメーターとして渡され、拡張ウィザードがこの要素の内容を使用できるようになります。  このデータに対する検証は行われません。  
  
 `WizardData` 要素の内容は渡されますが、変更されずに、`IWizard.RunStarted` メソッドにあるパラメーターの文字列ディクショナリの中にあるパラメーターとして渡されます。  パラメーターは $WizardData$ という名前になります。  
  
## 使用例  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows アプリケーションでの標準プロジェクト テンプレートのメタデータの例を次に示します。  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
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
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
    <WizardData>  
        <!-- XML to pass to the custom wizard extension -->  
    </WizardData>  
</VSTemplate>  
```  
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [WizardExtension 要素 \(Visual Studio テンプレート\)](../extensibility/wizardextension-element-visual-studio-templates.md)   
 [方法 : プロジェクト テンプレートを組み合わせたウィザードを使用する](../extensibility/how-to-use-wizards-with-project-templates.md)