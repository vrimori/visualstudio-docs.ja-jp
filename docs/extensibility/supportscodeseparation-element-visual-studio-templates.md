---
title: "SupportsCodeSeparation 要素 (Visual Studio テンプレート) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation"
helpviewer_keywords: 
  - "<SupportsCodeSeparation> 要素 [Visual Studio テンプレート]"
  - "SupportsCodeSeparation 要素 [Visual Studio テンプレート]"
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# SupportsCodeSeparation 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**\[新しい項目の追加\]** ダイアログ ボックスの **\[別のファイルにコードを書き込む\]** チェック ボックスを有効にするかどうかを指定します。  
  
## 構文  
  
```  
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素。<br /><br /> テンプレートをカテゴリに分類し、**\[新しいプロジェクト\]** ダイアログ ボックス、または **\[新しいアイテム\]** ダイアログ ボックスでどのように表示させるかを定義します。|  
  
## テキスト値  
 テキスト値が必要です。  
  
 `true` または `false` のいずれかを設定する必要があります。これは、**\[新しい項目の追加\]** ダイアログ ボックスの **\[別のファイルにコードを書き込む\]** チェック ボックスを有効にするかどうかを示します。  
  
## 解説  
 `SupportsCodeSeparation` は、省略可能な要素です。  既定値 `false` です。  
  
 `SupportsCodeSeparation` 要素は、Web 項目テンプレートでのみ使用できます。  
  
 コード分離または分離コード ページ モデルでは、マークアップとプログラミング コードをそれぞれ別のファイルに格納できます。  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] と他の .NET 言語はこのモデルを使用します。  
  
## 使用例  
 **\[別のファイルにコードを書き込む\]** オプションを表示するよう指定する例を次に示します。  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsCodeSeparation>true</SupportsCodeSeparation>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)