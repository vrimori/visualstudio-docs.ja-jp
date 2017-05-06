---
title: "ProjectItem Element"
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
  - "ProjectItem element"
ms.assetid: df588235-12a1-4798-bc56-ef81843de17f
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# ProjectItem Element
  SharePoint プロジェクト項目を表します。  .spdata ファイルの必須のルート要素です。  
  
## 構文  
  
```  
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"  
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"  
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"  
    SupportedTrustLevels = "Trust levels that the project item supports"  
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"  
    Type="Identifier for the project item">  
  <Files>...</Files>  
  <ProjectItemFolder>...</ProjectItemFolder>  
  <SafeControls>...</SafeControls>  
  <FeatureProperties>...</FeatureProperties>  
  <ExtensionData>...</ExtensionData>  
</ProjectItem>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|**DefaultFile**|省略可能な **xs:string** 属性です。<br /><br /> **ソリューション エクスプローラー**で SharePoint プロジェクト項目を開いたときに Visual Studio エディターで開かれるファイルの相対パス \(ファイル名を含む\) です。  .spdata ファイルを格納するフォルダーからの相対パスを指定します。|  
|**FeatureReceiverClass**|省略可能な **xs:string** 属性です。<br /><br /> この SharePoint プロジェクト項目のフィーチャー レシーバー クラスの完全修飾名です。  フィーチャー レシーバーの詳細については、「[プロジェクト項目でのパッケージ化と配置の情報の提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)」を参照してください。|  
|**FeatureReceiverAssembly**|省略可能な **xs:string** 属性です。<br /><br /> この SharePoint プロジェクト項目のフィーチャー レシーバーを定義するアセンブリの完全修飾名を指定します。  フィーチャー レシーバーの詳細については、「[プロジェクト項目でのパッケージ化と配置の情報の提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)」を参照してください。  アセンブリの完全修飾名の詳細については、「[アセンブリ名](../Topic/Assembly%20Names.md)」を参照してください。|  
|**SupportedTrustLevels**|省略可能な **xs:string** 属性です。<br /><br /> この SharePoint プロジェクト項目でサポートする信頼レベルを指定します。  この値には、Sandboxed、FullTrust、All のいずれかの値を指定できます。  値 All を指定した場合は、Sandboxed と FullTrust の両方を指定したことになります。<br /><br /> カスタムの SharePoint プロジェクト項目の種類では、この属性の値は、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> メソッドの実装の <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> プロパティに割り当てる値に対応します。  この属性に別の値を指定した場合、その値は、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> プロパティに指定したものと同じ信頼レベルを指定するように上書きされます。|  
|**SupportedDeploymentScopes**|省略可能な **xs:string** 属性です。<br /><br /> この SharePoint プロジェクト項目でサポートする配置スコープを指定します。  この値は、Farm、Site、Web、WebApplication、Package のうちの 1 つ以上の文字列で構成されるコンマ区切りの文字列です。  たとえば、"Web, Site" などです。<br /><br /> カスタムの SharePoint プロジェクト項目の種類では、この属性の値は、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> メソッドの実装の <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> プロパティに割り当てる値に対応します。  この属性に別の値を指定した場合、その値は、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> プロパティに指定したものと同じ信頼レベルを指定するように上書きされます。|  
|**Type**|必須の **xs:string** 属性です。<br /><br /> SharePoint プロジェクト項目の識別子です。  カスタムの SharePoint プロジェクト項目の種類では、この識別子は、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> に渡す文字列になります。  詳細については、「[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)」を参照してください。<br /><br /> Visual Studio に付属する組み込みの SharePoint プロジェクト項目に対する識別子の一覧については、「[Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)」を参照してください。|  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|省略可能な要素です。<br /><br /> SharePoint プロジェクト項目に関連付けられているカスタム データ項目のコレクションを表します。<br /><br /> **ExtensionData** 要素は 1 つしか指定できません。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|省略可能な要素です。<br /><br /> フィーチャーが SharePoint に配置されるときに一緒に含まれるプロパティの値のコレクションを表します。<br /><br /> **FeatureProperties** 要素は 1 つしか指定できません。|  
|[&#91;ファイル&#93;](../sharepoint/files-element.md)|省略可能な **FileCollectionType** 要素です。<br /><br /> フィーチャー要素ファイルや SharePoint プロジェクト以外の依存プロジェクトの出力など、SharePoint プロジェクト項目と一緒に配置するファイルを指定します。<br /><br /> **Files** 要素と **ProjectItemFolder** 要素はどちらかを必ず指定する必要がありますが、両方指定することはできません。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|省略可能な **ProjectItemFolderType** 要素です。<br /><br /> マップされたフォルダーを表します。<br /><br /> **Files** 要素と **ProjectItemFolder** 要素はどちらかを必ず指定する必要がありますが、両方指定することはできません。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|省略可能な要素です。<br /><br /> SharePoint サイトの任意の ASPX ページ上で任意のユーザーが利用するうえで安全として指定されている ASPX コントロールと Web パーツのコレクションを表します。<br /><br /> **SafeControls** 要素は 1 つしか指定できません。|  
  
### 親要素  
 なし。  
  
## 要素情報  
  
|||  
|-|-|  
|**名前空間**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目スキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空も使用できる**|Ｘ|  
  
## 参照  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  