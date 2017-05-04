---
title: "FeatureProperty Element | Microsoft Docs"
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
  - "FeatureProperty element"
ms.assetid: 36a771a6-98d0-4a40-a278-d76baea82452
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# FeatureProperty Element
  フィーチャーが SharePoint に配置されるときに一緒に含まれるカスタム プロパティを表します。  フィーチャーが配置されると、そのプロパティにコードでアクセスできるようになります。  
  
## 構文  
  
```  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|**Key**|必須の **xs:string** 属性です。<br /><br /> プロパティ値を格納および取得するために使用するキー。  各プロパティには、フィーチャー内で一意であるキーが必要です。|  
|**Value**|必須の **xs:string** 属性です。<br /><br /> プロパティ値。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|フィーチャーが SharePoint に配置されるときに一緒に含まれるプロパティの値のコレクションを表します。|  
  
## 解説  
 フィーチャーのプロパティの詳細については、「[プロジェクト項目でのパッケージ化と配置の情報の提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)」を参照してください。  
  
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
  
  