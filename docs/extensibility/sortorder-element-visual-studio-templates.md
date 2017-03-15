---
title: "SortOrder 要素 (Visual Studio テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder"
helpviewer_keywords: 
  - "<SortOrder> 要素 [Visual Studio テンプレート]"
  - "SortOrder 要素 [Visual Studio テンプレート]"
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# SortOrder 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

同じカテゴリ内のテンプレートを並べ替えるための値を指定します。これは **\[新しいプロジェクト\]** ダイアログ ボックスまたは **\[新しい項目の追加\]** ダイアログ ボックスで表示されるときの順番になります。  
  
## 構文  
  
```  
<SortOrder> ... </SortOrder>  
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
  
 順序を示す `integer` を設定します。  
  
## 解説  
 `SortOrder` は、省略可能な要素です。  既定値は 100 です。値はすべて 10 の倍数である必要があります。  
  
 `SortOrder` 要素は、ユーザーが作成したテンプレートでは無視されます。  ユーザーによって作成されたテンプレートはすべてアルファベット順に並べ替えられます。  
  
 順序の値が低いテンプレートから順に **\[新しいプロジェクト\]** ダイアログ ボックス または **\[新しい項目の追加\]** ダイアログ ボックスに表示されます。  
  
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
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 この例では、`SortOrder` 要素に比較的大きい数値が入っています。  他の [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 項目テンプレートは、`290` よりも低い `SortOrder` 値になる場合がほとんどなので、このテンプレートよりも先に **\[新しいアイテム\]** ダイアログ ボックスに表示されます。  
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)