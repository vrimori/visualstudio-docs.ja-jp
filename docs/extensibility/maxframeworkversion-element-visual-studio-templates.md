---
title: "MaxFrameworkVersion 要素 (Visual Studio テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<MaxFrameworkVersion> 要素 (Visual Studio テンプレート)"
  - "MaxFrameworkVersion 要素 (Visual Studio テンプレート)"
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# MaxFrameworkVersion 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テンプレートで必要な .NET Framework の最大のバージョンを指定します。  これにより、**\[新しいプロジェクトの追加\]** ダイアログ ボックスの **\[対象の Framework バージョン\]** ボックスで選択された値に基づいて、テンプレートが **\[新しいプロジェクトの追加\]** ダイアログ ボックスの **\[テンプレート\]** セクションに表示されるかどうかが決まります。  
  
## 構文  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
  
 このテキストは、テンプレートで許可される .NET Framework の最上位のバージョン番号である必要があります。  
  
## 解説  
 `MaxFrameworkVersion` は、省略可能な要素です。  .vstemplate ファイルの `TemplateData` セクションの要素は、**\[新しいプロジェクトの追加\]** ダイアログ ボックスの **\[テンプレート\]** セクションのフィルターとして機能します。  **\[新しいプロジェクトの追加\]** ダイアログ ボックスの **\[対象の Framework バージョン\]** ボックスで選択された値に基づいて、.NET Framework の要件が `MaxFrameworkVersion` 要素の値より小さいテンプレートのみが表示されます。  新しいバージョンの .NET Framework と共に使用されたときにテンプレートが不用意に表示されることを防ぐため、必要な場合以外は `MaxFrameworkVersion` 要素を省略してください。  
  
## 使用例  
 標準的な [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] クラス テンプレートのメタデータの例を次に示します。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 この例では、テンプレートで必要な .NET Framework の最大バージョン \(`MaxFrameworkVersion`\) は 3.5 です。  このテンプレートは、**\[新しいプロジェクトの追加\]** ダイアログ ボックスの **\[対象の Framework バージョン\]** ボックスで 3.0 または 3.5 を選択した場合にのみ表示されます。  
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)