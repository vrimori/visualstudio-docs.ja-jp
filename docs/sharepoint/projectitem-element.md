---
title: ProjectItem 要素 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: f6d273e0fa980e25c8b8d0c7ea6b1a8eb5d537c9
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692042"
---
# <a name="projectitem-element"></a>ProjectItem 要素
  SharePoint プロジェクト項目を表します。 この要素は、必要なファイルのルート要素 the.spdata です。  
  
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
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**DefaultFile**|省略可能な**xs: 文字列**属性。<br /><br /> 相対パスでの SharePoint プロジェクト項目を開くときに、Visual Studio エディターで開かれているファイルのファイル名を含む**ソリューション エクスプ ローラー**です。 パスが含まれているフォルダーから相対、`.spdata`ファイル。|  
|**FeatureReceiverClass**|省略可能な**xs:string**属性。<br /><br /> この SharePoint プロジェクト アイテムのフィーチャー レシーバー クラスの完全修飾名。 フィーチャー レシーバーの詳細については、次を参照してください。[を提供するパッケージとプロジェクト項目での展開情報](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)です。|  
|**FeatureReceiverAssembly**|省略可能な**xs:string**属性。<br /><br /> この SharePoint プロジェクト アイテムのフィーチャー レシーバーを定義するアセンブリの完全修飾名を指定します。 フィーチャー レシーバーの詳細については、次を参照してください。[を提供するパッケージとプロジェクト項目での展開情報](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)です。 完全修飾アセンブリ名の詳細については、次を参照してください。[アセンブリ名](/dotnet/framework/app-domains/assembly-names)です。|  
|**SupportedTrustLevels**|省略可能な**xs:string**属性。<br /><br /> この SharePoint プロジェクト アイテムをサポートしている信頼レベルを指定します。 この値は、次の文字列のいずれかを指定できます。 サンド ボックス化された、FullTrust、またはすべて。 値 Sandboxed と FullTrust All を指定します。<br /><br /> カスタム SharePoint プロジェクト項目の種類、この属性の値に割り当てられる値に対応、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>プロパティの実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>メソッドです。 Visual Studio で指定した同じ信頼レベルを指定するために、値が上書きされますこの属性に別の値を指定する場合、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>プロパティです。|  
|**SupportedDeploymentScopes**|省略可能な**xs:string**属性。<br /><br /> この SharePoint プロジェクト アイテムをサポートする配置のスコープを指定します。 この値は次の文字列の 1 つ以上ので構成されるコンマ区切りの文字列: ファーム、サイト、Web、web アプリケーション、またはパッケージです。 例: `Web, Site`<br /><br /> カスタム SharePoint プロジェクト項目の種類、この属性の値に割り当てられる値に対応、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>プロパティの実装で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>メソッドです。 Visual Studio で指定した同じ信頼レベルを指定するために、値が上書きされますこの属性に別の値を指定する場合、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>プロパティです。|  
|**Type**|必要な**xs:string**属性。<br /><br /> SharePoint プロジェクト項目の識別子。 カスタム SharePoint プロジェクト項目の種類、識別子が渡された文字列、<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>です。 詳細については、次を参照してください。[する方法: SharePoint プロジェクト項目の種類を定義する](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)です。<br /><br /> Visual Studio に含まれている組み込みの SharePoint プロジェクト項目の識別子の一覧は、次を参照してください。 [SharePoint プロジェクト項目の拡張](../sharepoint/extending-sharepoint-project-items.md)です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|省略可能な要素です。<br /><br /> SharePoint プロジェクト アイテムに関連付けられているカスタム データ項目のコレクションを表します。<br /><br /> 1 つだけを含めることができます**ExtensionData**要素。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|省略可能な要素です。<br /><br /> SharePoint に配置されるときに、機能に含まれているプロパティ値のコレクションを表します。<br /><br /> 1 つだけを含めることができます**FeatureProperties**要素。|  
|[ファイル](../sharepoint/files-element.md)|省略可能な**FileCollectionType**要素。<br /><br /> フィーチャー要素ファイルなど、SharePoint プロジェクト項目と依存する以外の SharePoint プロジェクトの出力を配置するファイルを指定します。<br /><br /> いずれかを含める、**ファイル**または**ProjectItemFolder**要素が、両方は使用できません。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|省略可能な**ProjectItemFolderType**要素。<br /><br /> マップされたフォルダーを表します。<br /><br /> いずれかを含める、**ファイル**または**ProjectItemFolder**要素が、両方は使用できません。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|省略可能な要素です。<br /><br /> ASPX コントロールと、SharePoint サイト上の任意の ASPX ページにアクセスするすべてのユーザーのセキュリティで保護されたとして指定されている Web パーツのコレクションを表します。<br /><br /> 1 つだけを含めることができます**SafeControls**要素。|  
  
### <a name="parent-elements"></a>親要素  
 なし。  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|**名前空間**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|いいえ|  
  
## <a name="see-also"></a>関連項目  
 [SharePoint プロジェクト項目スキーマのリファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  