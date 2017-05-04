---
title: "ProjectItemFile Element | Microsoft Docs"
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
  - "ProjectItemFile element"
ms.assetid: 68d44d31-625a-4f02-b998-463ac0ffb2ef
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ProjectItemFile Element
  プロジェクト項目が SharePoint に配置されるときに一緒に含まれる SharePoint ファイル \(フィーチャー要素ファイルなど\) を表します。  
  
## 構文  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## 型  
 **ProjectItemFileType**  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|**Source**|必須の **xs:string** 属性です。<br /><br /> プロジェクト項目と一緒に配置するファイルの名前。|  
|**Target**|省略可能な **xs:string** 属性です。<br /><br /> ファイルの配置先となる SharePoint 上のパス。配置ルート フォルダーを基準とする相対パスです。  配置ルート フォルダーは、**Type** 属性で指定されている配置タイプによって決まります。  **Target** 属性が指定されていない場合、ファイルの配置先は、**Source** 属性で指定されている名前のフォルダーになります。<br /><br /> 詳細については、「[Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)」の SharePoint プロジェクト項目の **Deployment Path** プロパティおよび **Deployment Root** プロパティに関する説明を参照してください。|  
|**Type**|必須の **xs:string** 属性です。<br /><br /> ファイルの配置のタイプ。  使用できる値の詳細については、「[Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)」の SharePoint プロジェクト項目の **Deployment Type** プロパティに関する説明を参照してください。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[&#91;ファイル&#93;](../sharepoint/files-element.md)|SharePoint プロジェクト項目が SharePoint に配置されるときに一緒に含まれるファイルを指定します。|  
  
## 解説  
 **ProjectItemFile** 要素で通常は参照される SharePoint ファイルには、フィーチャー要素ファイル \(Elements.xml\)、リスト定義のスキーマ ファイル \(Schema.xml\)、および Web パーツの Web パーツ定義ファイル \(.webpart\) があります。  
  
## 要素情報  
  
|||  
|-|-|  
|**名前空間**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目スキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空も使用できる**|Ｘ|  
  
## 参照  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  