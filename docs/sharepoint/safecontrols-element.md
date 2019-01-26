---
title: SafeControls 要素 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f2819f0e913b9078f22482fb39164e8ba8d40da
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866505"
---
# <a name="safecontrols-element"></a>SafeControls 要素
  ASPX のコレクションを制御し、として指定されている Web パーツを SharePoint サイトのいずれかの ASPX ページにアクセスするすべてのユーザーに対してセキュリティで保護します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<SafeControls>  
  <SafeControl.../>  
</SafeControls>  
```  
  
## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素
  
|要素|説明|  
|-------------|-----------------|  
|[SafeControl](../sharepoint/safecontrol-element.md)|省略可能な要素です。<br /><br /> ASPX コントロールまたは SharePoint サイトのいずれかの ASPX ページにアクセスするすべてのユーザーに対してセキュリティで保護されたとして指定されている Web パーツを表します。|  
  
### <a name="parent-elements"></a>親要素
  
|要素|説明|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクト項目を表します。 この要素の必須のルート要素の *.spdata*ファイル。|  
  
## <a name="remarks"></a>Remarks  
 安全なコントロールの詳細については、次を参照してください。[プロジェクト項目でパッケージ化と配置の情報を提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)します。  
  
## <a name="element-information"></a>要素情報
  
|||  
|-|-|  
|**Namespace**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>SharePointProjectItemModel SharePointTools/2010/|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**ファイルの検証**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|いいえ|  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクト項目スキーマのリファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [プロジェクト項目でパッケージ化と配置の情報を提供します。](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
