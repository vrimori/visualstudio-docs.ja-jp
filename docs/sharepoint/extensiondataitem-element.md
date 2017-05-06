---
title: "ExtensionDataItem Element"
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
  - "ExtensionDataItem element"
ms.assetid: 6a5fe7eb-b433-42dc-bd50-4882b780e2fb
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ExtensionDataItem Element
  SharePoint プロジェクト項目に関連付けられているカスタム データ項目のコレクションを、キー\/値の形式で表します。  キーと値は両方とも文字列である必要があります。  
  
## 構文  
  
```  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|**Key**|必須の **xs:string** 属性です。<br /><br /> データ項目を格納および取得するために使用するキー。|  
|**Value**|必須の **xs:string** 属性です。<br /><br /> データ項目の値。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|SharePoint プロジェクト項目に関連付けられているカスタム データ項目のコレクションを表します。|  
  
## 解説  
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> プロパティを使用してカスタム データを SharePoint プロジェクト項目に関連付けると、そのデータは、プロジェクト項目の .spdata ファイルの新しい **ExtensionDataItem** 要素に保存されます。  詳細については、「[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)」を参照してください。  
  
## 要素情報  
  
|||  
|-|-|  
|**名前空間**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目スキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空も使用できる**|Ｘ|  
  
## 参照  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  