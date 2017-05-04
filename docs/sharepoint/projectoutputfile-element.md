---
title: "ProjectOutputFile Element | Microsoft Docs"
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
  - "ProjectOutputFile element"
ms.assetid: 52a017bf-e19c-49e4-bb8f-cbe6958195c2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# ProjectOutputFile Element
  プロジェクト項目が SharePoint に配置されるときに一緒に含まれる個別のプロジェクトの出力を表します。  
  
## 構文  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## 型  
 **ProjectOutputFileType**  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|**ProjectId**|必須の **xs:string** 属性です。<br /><br /> 依存プロジェクトの GUID。この依存プロジェクトの出力が含まれます。  この値は、依存プロジェクト ファイル内の **ProjectGuid** 要素に対応します。|  
|**ProjectPath**|必須の **xs:string** 属性です。<br /><br /> 依存プロジェクトの相対パス \(プロジェクト ファイル名を含む\)。この依存プロジェクトの出力が含まれます。  このパスは、SharePoint プロジェクト項目が含まれる SharePoint プロジェクトのルート フォルダーを基準とする相対パスです。|  
|**Target**|省略可能な **xs:string** 属性です。<br /><br /> 依存プロジェクトの出力が配置される SharePoint サーバー上のパス。配置ルート フォルダーを基準とする相対パスです。  配置ルート フォルダーは、**Type** 属性で指定されている配置タイプによって決まります。<br /><br /> 詳細については、「[Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)」の SharePoint プロジェクト項目の **Deployment Path** プロパティおよび **Deployment Root** プロパティに関する説明を参照してください。|  
|**Type**|必須の **xs:string** 属性です。<br /><br /> 依存プロジェクトの出力に使用する配置のタイプ。  使用できる値の詳細については、「[Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)」の SharePoint プロジェクト項目の **Deployment Type** プロパティに関する説明を参照してください。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[&#91;ファイル&#93;](../sharepoint/files-element.md)|SharePoint プロジェクト項目が SharePoint に配置されるときに一緒に含まれるファイルを指定します。|  
  
## 解説  
 SharePoint プロジェクト項目の配置にプロジェクトの出力を含めるには、**ProjectOutputFile** 要素を使用します。  別のプロジェクトを指定することも、プロジェクト項目を含むプロジェクトと同じプロジェクトを指定することもできます。  詳細については、「[プロジェクト項目でのパッケージ化と配置の情報の提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)」を参照してください。  
  
## 要素情報  
  
|||  
|-|-|  
|**名前空間**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目スキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空も使用できる**|Ｘ|  
  
## 参照  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [プロジェクト項目でのパッケージ化と配置の情報の提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  