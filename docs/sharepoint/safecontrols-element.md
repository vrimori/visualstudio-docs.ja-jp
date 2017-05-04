---
title: "SafeControls Element | Microsoft Docs"
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
  - "SafeControls element"
ms.assetid: f5ffdbbe-cf85-4e5a-9d39-3cd4462f2a0e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# SafeControls Element
  SharePoint サイトの任意の ASPX ページ上で任意のユーザーが利用するうえで安全として指定されている ASPX コントロールと Web パーツのコレクションを表します。  
  
## 構文  
  
```  
<SafeControls>  
  <SafeControl.../>  
</SafeControls>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[SafeControl](../sharepoint/safecontrol-element.md)|省略可能な要素です。<br /><br /> SharePoint サイトの任意の ASPX ページ上で任意のユーザーが利用するうえで安全として指定されている ASPX コントロールまたは Web パーツを表します。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクト項目を表します。  .spdata ファイルの必須のルート要素です。|  
  
## 解説  
 安全なコントロールの詳細については、「[プロジェクト項目でのパッケージ化と配置の情報の提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)」を参照してください。  
  
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
  
  