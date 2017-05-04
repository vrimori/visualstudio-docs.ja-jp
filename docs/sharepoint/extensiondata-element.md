---
title: "ExtensionData Element | Microsoft Docs"
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
  - "ExtensionData element"
ms.assetid: caf6843b-dcf5-4688-a9eb-a424aae1beab
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# ExtensionData Element
  SharePoint プロジェクト項目に関連付けられているカスタム データ項目のコレクションを表します。  
  
## 構文  
  
```  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|省略可能な要素です。<br /><br /> SharePoint プロジェクト項目に関連付けられているカスタム データ項目のコレクションを、キー\/値の形式で表します。  キーと値は両方とも文字列である必要があります。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクト項目を表します。  .spdata ファイルの必須のルート要素です。|  
  
## 解説  
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> プロパティを使用してカスタム データを SharePoint プロジェクト項目に関連付けると、そのデータは、プロジェクト項目の .spdata ファイルの **ExtensionData** 要素に保存されます。  詳細については、「[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)」を参照してください。  
  
## 要素情報  
  
|||  
|-|-|  
|**名前空間**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目スキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空も使用できる**|Ｘ|  
  
## 参照  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  