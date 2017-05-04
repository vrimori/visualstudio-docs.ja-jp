---
title: "SafeControl Element | Microsoft Docs"
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
  - "SafeControl element"
ms.assetid: e7c61749-fc73-412c-be30-4af5ff2a9fd2
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# SafeControl Element
  SharePoint サイトの任意の ASPX ページ上で任意のユーザーが利用するうえで安全として指定されている ASPX コントロールまたは Web パーツを表します。  
  
## 構文  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|**Assembly**|省略可能な **xs:string** 属性です。<br /><br /> ASPX コントロールまたは Web パーツが定義されているアセンブリの名前です。  既定では、このアセンブリ名には、置き換え可能パラメーターである **$SharePoint.Project.AssemblyFullName$** が使用されます。  詳細については、「[置き換え可能パラメーター](../sharepoint/replaceable-parameters.md)」を参照してください。|  
|**IsSafe**|省略可能な **xs:boolean** 属性です。<br /><br /> ASPX コントロールまたは Web パーツが安全であり、信頼されていないユーザーがアクセスできるかどうかを指定します。|  
|**IsSafeAgainstScript**|省略可能な **xs:boolean** 属性です。<br /><br /> 信頼されていないユーザーが ASPX コントロールまたは Web パーツのプロパティを表示したり編集したりできるかどうかを指定します。|  
|**Name**|省略可能な **xs:string** 属性です。<br /><br /> コレクション内のこの安全なコントロール エントリの名前です。|  
|**Namespace**|省略可能な **xs:string** 属性です。<br /><br /> ASPX コントロールまたは Web パーツの名前空間です。|  
|**TypeName**|省略可能な **xs:string** 属性です。<br /><br /> ASPX コントロールまたは Web パーツの型名です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|SharePoint サイトの任意の ASPX ページ上で任意のユーザーが利用するうえで安全として指定されている ASPX コントロールと Web パーツのコレクションを表します。|  
  
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
  
  