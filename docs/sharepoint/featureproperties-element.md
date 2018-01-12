---
title: "FeatureProperties 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: FeatureProperties element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e710c5a73fbee0a09fb69518def1b03e353661c8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="featureproperties-element"></a>FeatureProperties 要素
  SharePoint に配置されるときに、機能に含まれているプロパティ値のコレクションを表します。 フィーチャーが配置されると、プロパティの値をコードでアクセスできます。  
  
## <a name="syntax"></a>構文  
  
```  
<FeatureProperties>  
  <FeatureProperty.../>  
</FeatureProperties>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|省略可能な要素です。<br /><br /> キー/値の形式でのカスタム プロパティを表します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクト項目を表します。 .Spdata ファイルの必要なルート要素です。|  
  
## <a name="remarks"></a>コメント  
 フィーチャーのプロパティの詳細については、次を参照してください。[を提供するパッケージとプロジェクト項目での展開情報](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)です。  
  
## <a name="element-information"></a>要素情報  
  
|要素|説明|  
|-------------|-----------------|  
|**名前空間**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|×|  
  
## <a name="see-also"></a>参照  
 [SharePoint プロジェクト項目のスキーマ リファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [プロジェクト項目でのパッケージ化と配置の情報の提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  