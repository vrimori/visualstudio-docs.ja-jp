---
title: ProjectItem 要素 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e7c9a32a7fa84d8adc064aa3a3ac035999295791
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890103"
---
# <a name="projectitem-element"></a>ProjectItem 要素
  SharePoint プロジェクト項目を表します。 この要素の必須のルート要素の *.spdata*ファイル。  
  
## <a name="syntax"></a>構文  
  
```xml  
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
  
## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**DefaultFile**|省略可能な**xs: 文字列**属性。<br /><br /> SharePoint プロジェクト項目を開くときに、Visual Studio エディターで表示されるファイルのファイル名を含む、相対パス**ソリューション エクスプ ローラー**します。 含むフォルダーからの相対パスでは、 *.spdata*ファイル。|  
|**FeatureReceiverClass**|省略可能な**xs:string**属性。<br /><br /> この SharePoint プロジェクト アイテムのフィーチャー レシーバー クラスの完全修飾名。 フィーチャー レシーバーの詳細については、次を参照してください。[プロジェクト項目でパッケージ化と配置の情報を提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)します。|  
|**FeatureReceiverAssembly**|省略可能な**xs:string**属性。<br /><br /> この SharePoint プロジェクト アイテムのフィーチャー レシーバーを定義するアセンブリの完全修飾名を指定します。 フィーチャー レシーバーの詳細については、次を参照してください。[プロジェクト項目でパッケージ化と配置の情報を提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)します。 完全修飾アセンブリ名の詳細については、次を参照してください。[アセンブリ名](/dotnet/framework/app-domains/assembly-names)します。|  
|**SupportedTrustLevels**|省略可能な**xs:string**属性。<br /><br /> この SharePoint プロジェクト アイテムがサポートされる信頼レベルを指定します。 この値は、次の文字列のいずれかを指定できます。サンド ボックス化された、FullTrust、またはすべて。 値 All は、Sandboxed および FullTrust の両方を指定します。<br /><br /> カスタム SharePoint プロジェクト項目の種類、この属性の値に割り当てた値に対応、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>プロパティの実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>メソッド。 Visual Studio で指定した同じ信頼レベルを指定するために、値が上書きされますこの属性に別の値を指定する場合、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>プロパティ。|  
|**SupportedDeploymentScopes**|省略可能な**xs:string**属性。<br /><br /> この SharePoint プロジェクト アイテムをサポートする展開のスコープを指定します。 この値は、次の文字列の 1 つ以上で構成されるコンマ区切りの文字列です。ファーム、サイト、Web、web アプリケーション、またはパッケージです。 例: `Web, Site`<br /><br /> カスタム SharePoint プロジェクト項目の種類、この属性の値に割り当てた値に対応、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>プロパティの実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>メソッド。 Visual Studio で指定した同じ信頼レベルを指定するために、値が上書きされますこの属性に別の値を指定する場合、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>プロパティ。|  
|**Type**|必要な**xs:string**属性。<br /><br /> SharePoint プロジェクト アイテムの識別子。 カスタム SharePoint プロジェクト項目の種類、識別子は文字列に渡す、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>します。 詳細については、「[方法 :SharePoint プロジェクト項目の種類定義](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)します。<br /><br /> Visual Studio に含まれている組み込みの SharePoint プロジェクト アイテムの識別子の一覧は、次を参照してください。[拡張の SharePoint プロジェクト アイテム](../sharepoint/extending-sharepoint-project-items.md)します。|  
  
### <a name="child-elements"></a>子要素
  
|要素|説明|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|省略可能な要素です。<br /><br /> SharePoint プロジェクト アイテムに関連付けられているカスタム データ項目のコレクションを表します。<br /><br /> 1 つだけ含めることができます**ExtensionData**要素。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|省略可能な要素です。<br /><br /> SharePoint に配置されるときに、機能に含まれているプロパティ値のコレクションを表します。<br /><br /> 1 つだけ含めることができます**FeatureProperties**要素。|  
|[ファイル](../sharepoint/files-element.md)|省略可能な**FileCollectionType**要素。<br /><br /> SharePoint プロジェクト項目の 機能の要素ファイルなど、および SharePoint 以外の依存プロジェクトの出力と共に配置するファイルを指定します。<br /><br /> いずれかを含める、**ファイル**または**ProjectItemFolder**両方ではなく、要素。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|省略可能な**ProjectItemFolderType**要素。<br /><br /> マップされたフォルダーを表します。<br /><br /> いずれかを含める、**ファイル**または**ProjectItemFolder**両方ではなく、要素。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|省略可能な要素です。<br /><br /> ASPX コントロールと、SharePoint サイト上のいずれかの ASPX ページにアクセスするすべてのユーザーに対してセキュリティで保護されたとして指定されている Web パーツのコレクションを表します。<br /><br /> 1 つだけ含めることができます**SafeControls**要素。|  
  
### <a name="parent-elements"></a>親要素
 なし。  
  
## <a name="element-information"></a>要素情報
  
|||  
|-|-|  
|**Namespace**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>SharePointProjectItemModel SharePointTools/2010/|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**ファイルの検証**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|いいえ|  
  
## <a name="see-also"></a>関連項目
[SharePoint プロジェクト項目スキーマ rseference](../sharepoint/sharepoint-project-item-schema-reference.md)  
