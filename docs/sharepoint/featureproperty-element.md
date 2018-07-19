---
title: FeatureProperty 要素 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ccc9e0d628d5c17283368de135c8e83dbd40bec1
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325983"
---
# <a name="featureproperty-element"></a>FeatureProperty 要素
  SharePoint に配置されるときに、機能に含まれているカスタム プロパティを表します。 フィーチャーが配置されると、コードでプロパティにアクセスすることができます。  
  
## <a name="syntax"></a>構文  
  
```xml  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**Key**|必要な**xs:string**属性。<br /><br /> このキーは、格納およびプロパティの値を取得するために使用します。 各プロパティが、機能内で一意キーが必要です。|  
|**[値]**|必要な**xs:string**属性。<br /><br /> プロパティ値。|  
  
### <a name="child-elements"></a>子要素
 なし。  
  
### <a name="parent-elements"></a>親要素
  
|要素|説明|  
|-------------|-----------------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|SharePoint に配置されるときに、機能に含まれているプロパティ値のコレクションを表します。|  
  
## <a name="remarks"></a>Remarks  
 機能プロパティの詳細については、次を参照してください。[プロジェクト項目でのパッケージと展開の情報を提供する](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)します。  
  
## <a name="element-information"></a>要素情報
  
|||  
|-|-|  
|**名前空間**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>SharePointProjectItemModel SharePointTools/2010/|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**ファイルの検証**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|いいえ|  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクト項目スキーマのリファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [プロジェクト項目でパッケージ化と配置の情報を提供します。](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  
