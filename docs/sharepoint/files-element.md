---
title: "Files Element | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Files element"
ms.assetid: 3c611d5b-28f1-48a7-a068-63e01fa2f3aa
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Files Element
  フィーチャー要素ファイルや SharePoint プロジェクト以外の依存プロジェクトの出力など、SharePoint プロジェクト項目と一緒に配置するファイルを指定します。  
  
## 構文  
  
```  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## 型  
 **FileCollectionType**  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|省略可能な **ProjectItemFileType** 要素。<br /><br /> プロジェクト項目が SharePoint に配置されるときに一緒に含まれる SharePoint ファイル \(フィーチャー要素ファイルなど\) を表します。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|省略可能な **ProjectOutputFileType** 要素。<br /><br /> プロジェクト項目が SharePoint に配置されるときに一緒に含まれるプロジェクトの出力を表します。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクト項目を表します。  .spdata ファイルの必須のルート要素です。|  
  
## 要素情報  
  
|||  
|-|-|  
|**名前空間**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目スキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空も使用できる**|Ｘ|  
  
## 参照  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  