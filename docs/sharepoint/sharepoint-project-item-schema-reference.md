---
title: "SharePoint Project Item Schema Reference | Microsoft Docs"
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
  - "SafeControls element"
  - "SafeControl element"
  - ".spdata files"
  - "ExtensionData element"
  - "FeatureProperties element"
  - "ProjectOutputFile element"
  - "Files element"
  - "ProjectItemFolder element"
  - "ProjectItemFile element"
  - "ExtensionDataItem element"
  - "ProjectItem element"
ms.assetid: 12b63cbc-bf94-4175-bfa8-2117943d00d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# SharePoint Project Item Schema Reference
  Visual Studio では、SharePoint プロジェクト項目スキーマを使用して、.spdata ファイルの内容を検証します。  .spdata ファイルは、SharePoint プロジェクト項目の内容と動作を指定します。  SharePoint プロジェクト項目の内容の詳細については、「[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)」を参照してください。  
  
 SharePoint プロジェクト項目スキーマは ProjectItemModelSchema.xsd という名前で、既定では、%Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas にインストールされます。  
  
 ルート要素は [ProjectItem](../sharepoint/projectitem-element.md) 要素です。  このスキーマで定義されているすべての要素の説明を次の表に示します。  
  
|要素|説明|  
|--------|--------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|SharePoint プロジェクト項目に関連付けられているカスタム データ項目のコレクションを表します。|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|SharePoint プロジェクト項目に関連付けられているカスタム データ項目のコレクションを、キー\/値の形式で表します。  キーと値は両方とも文字列である必要があります。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|フィーチャーが SharePoint に配置されるときに一緒に含まれるプロパティの値のコレクションを表します。  フィーチャーが配置されると、そのプロパティの値にコードでアクセスできるようになります。|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|フィーチャーが SharePoint に配置されるときに一緒に含まれるカスタム プロパティを表します。  フィーチャーが配置されると、そのプロパティにコードでアクセスできるようになります。|  
|[&#91;ファイル&#93;](../sharepoint/files-element.md)|フィーチャー要素ファイルやプロジェクトの出力など、SharePoint プロジェクト項目と一緒に配置するファイルを指定します。|  
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクト項目を表します。|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|プロジェクト項目が SharePoint に配置されるときに一緒に含まれる SharePoint ファイル \(フィーチャー要素ファイルなど\) を表します。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|マップされたフォルダーを表します。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|プロジェクト項目が SharePoint に配置されるときに一緒に含まれるプロジェクトの出力を表します。|  
|[SafeControl](../sharepoint/safecontrol-element.md)|SharePoint サイトの任意の ASPX ページ上で任意のユーザーが利用するうえで安全として指定されている ASPX コントロールまたは Web パーツを表します。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|SharePoint サイトの任意の ASPX ページ上で任意のユーザーが利用するうえで安全として指定されている ASPX コントロールと Web パーツのコレクションを表します。|  
  
## 参照  
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  