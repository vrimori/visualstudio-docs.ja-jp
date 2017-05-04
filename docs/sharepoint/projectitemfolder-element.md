---
title: "ProjectItemFolder Element | Microsoft Docs"
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
  - "ProjectItemFolder element"
ms.assetid: 15b386dd-f523-4425-9fcc-517325681358
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# ProjectItemFolder Element
  マップされたフォルダーを表します。  
  
## 構文  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## 型  
 **ProjectItemFolderType**  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|**Target**|必須の **xs:string** 属性です。<br /><br /> マップされたフォルダーを対応付ける SharePoint のフォルダーのパス。配置ルート フォルダーを基準とする相対パスです。  配置ルート フォルダーは、**Type** 属性で指定されている配置タイプによって決まります。<br /><br /> 詳細については、「[Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)」の SharePoint プロジェクト項目の **Deployment Path** プロパティおよび **Deployment Root** プロパティに関する説明を参照してください。|  
|**Type**|必須の **xs:string** 属性です。<br /><br /> マップされたフォルダーの配置のタイプ。  使用できる値の詳細については、「[Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)」の SharePoint プロジェクト項目の **Deployment Type** プロパティに関する説明を参照してください。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクト項目を表します。  .spdata ファイルの必須のルート要素です。|  
  
## 解説  
 マップされたフォルダーの詳細については、「[方法: マップされたフォルダーを追加および削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)」を参照してください。  
  
## 要素情報  
  
|||  
|-|-|  
|**名前空間**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目スキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空も使用できる**|Ｘ|  
  
## 参照  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [方法: マップされたフォルダーを追加および削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  