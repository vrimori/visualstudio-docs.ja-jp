---
title: "ProjectItem 要素 (Visual Studio 項目テンプレート) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem> 要素 [Visual Studio 項目テンプレート]"
  - "ProjectItem 要素 [Visual Studio 項目テンプレート]"
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# ProjectItem 要素 (Visual Studio 項目テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

項目テンプレートに含まれているファイルを指定します。  
  
> [!NOTE]
>  `ProjectItem` 要素は、テンプレートがプロジェクト用かアイテム用かによって受け入れる属性が異なります。  ここでは、アイテムの `ProjectItem` 要素について説明します。  プロジェクト テンプレートの `ProjectItem` 要素については、「[ProjectItem 要素 \(Visual Studio プロジェクト テンプレート\)](../extensibility/projectitem-element-visual-studio-project-templates.md)」を参照してください。  
  
## 構文  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`SubType`|省略可能な属性です。<br /><br /> 複数ファイルの項目テンプレートにあるアイテムのサブタイプを指定します。  この値を使って、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がアイテムを開くときに使用するエディターを指定します。|  
|`CustomTool`|省略可能な属性です。<br /><br /> プロジェクト ファイルの項目の CustomTool を設定します。|  
|`ItemType`|省略可能な属性です。<br /><br /> プロジェクト ファイルの項目の ItemType を設定します。|  
|`ReplaceParameters`|省略可能な属性です。<br /><br /> ブール値を使用します。これは、プロジェクトがテンプレートから作成されるときに、置換する必要のあるパラメーター値がアイテムに存在するかどうかを指定します。  既定値は `false`です。|  
|`TargetFileName`|省略可能な属性です。<br /><br /> テンプレートから作成されるアイテムの名前を指定します。  この属性は、アイテム名を作成するためにパラメーター置換をする場合に便利です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|テンプレートの内容を指定します。|  
  
## テキスト値  
 テキスト値が必要です。  
  
 `string` は、テンプレート .zip ファイルにあるファイルの名前を示します。  
  
## 解説  
 `ProjectItem` は `TemplateContent` の省略可能な子要素です。  
  
 `TargetFileName` 属性は、パラメーターでファイルの名前を変更する場合にも使用できます。  たとえば、`MyFile.vb` というファイルがテンプレート .zip ファイルのルートにあるとします。このファイルを **\[新しい項目の追加\]** ダイアログ ボックスで入力したファイル名に基づいた名前に変更するには、次の XML を使用します。  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 このテンプレートからアイテムが作成されると、ファイルには **\[新しい項目の追加\]** ダイアログ ボックスで入力した名前に基づいた名前が付けられます。  これは、複数ファイルの項目テンプレートを作成する場合に便利です。  詳細については、「[方法 : 複数ファイルの項目テンプレートを作成する](../ide/how-to-create-multi-file-item-templates.md)」および「[テンプレート名](../ide/template-parameters.md)」を参照してください。  
  
## 使用例  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] クラスでの標準的な項目テンプレートのメタデータの例を次に示します。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [方法 : 複数ファイルの項目テンプレートを作成する](../ide/how-to-create-multi-file-item-templates.md)   
 [テンプレート名](../ide/template-parameters.md)