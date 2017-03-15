---
title: "ProvideDefaultName 要素 (Visual Studio テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName"
helpviewer_keywords: 
  - "ProvideDefaultName 要素 [Visual Studio プロジェクト テンプレート]"
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# ProvideDefaultName 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**\[新しい項目の追加\]** ダイアログ ボックス または **\[新しいプロジェクト\]** ダイアログ ボックスに表示される [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクト テンプレートに既定の名前を付けるかどうかを指定します。  
  
## 構文  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 `true` または `false` のいずれかを設定する必要があります。これは、**\[新しい項目の追加\]** ダイアログ ボックス または **\[新しいプロジェクト\]** ダイアログ ボックスに表示されるテンプレートに既定の名前を付けるかどうかを指定します。  
  
## 解説  
 `ProvideDefaultName` は、省略可能な要素です。  既定値は `true` です。  
  
 `ProvideDefaultName` 要素が `false` の場合、**\[新しい項目の追加\]** ダイアログ ボックス、および **\[新しいプロジェクト\]** ダイアログ ボックスの **\[プロジェクト名\/ファイル名\]** ボックスは「`<Enter_name>`」と入力された状態で表示されます。  
  
 [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) 要素を使用して、**\[新しい項目の追加\]** ダイアログ ボックス および **\[新しいプロジェクト\]** ダイアログ ボックス内のプロジェクトまたはアイテムの既定名を指定します。  
  
## 使用例  
 `ProvideDefaultName` 要素を `false` に設定するコード例を次に示します。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)