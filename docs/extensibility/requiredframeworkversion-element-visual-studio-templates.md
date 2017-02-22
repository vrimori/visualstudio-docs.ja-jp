---
title: "RequiredFrameworkVersion 要素 (Visual Studio テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<RequiredFrameworkVersion> (Visual Studio テンプレート)"
  - "RequiredFrameworkVersion (Visual Studio テンプレート)"
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# RequiredFrameworkVersion 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

template.Schema 階層で必要な .NET Framework の最小のバージョンを指定します。  
  
## 構文  
  
```  
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>  
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
  
 このテキストは、テンプレートで必要な .NET Framework の最小のバージョン番号である必要があります。  
  
## 解説  
 `RequiredFrameworkVersion` は、省略可能な要素です。  テンプレートが .NET Framework の特定の最小バージョンとそれ以降のバージョン \(ある場合\) のみをサポートする場合に、この要素を使用します。  
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [対象となる特定の .NET Framework バージョンの指定](../ide/targeting-a-specific-dotnet-framework-version.md)