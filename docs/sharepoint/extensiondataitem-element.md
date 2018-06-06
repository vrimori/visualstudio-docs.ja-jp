---
title: ExtensionDataItem 要素 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eb88c8adc3f32e428543e2bf1e0e80e9538678a2
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766508"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem 要素
  キー/値の形式で、SharePoint プロジェクト項目に関連付けられているカスタム データ項目。 キーと値の両方には、文字列がある場合があります。  
  
## <a name="syntax"></a>構文  
  
```xml  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**Key**|必要な**xs: 文字列**属性。<br /><br /> 格納およびデータ項目を取得するために使用するキー。|  
|**[値]**|必要な**xs:string**属性。<br /><br /> データ項目の値です。|  
  
### <a name="child-elements"></a>子要素
 なし。  
  
### <a name="parent-elements"></a>親要素
  
|要素|説明|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|SharePoint プロジェクト アイテムに関連付けられているカスタム データ項目のコレクションを表します。|  
  
## <a name="remarks"></a>コメント  
 ときにするデータを関連付けるカスタム SharePoint プロジェクト項目を使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>オブジェクト、Visual Studio を新しいデータを保存する**ExtensionDataItem**内の要素、`.spdata`ファイルで、プロジェクト項目です。 詳細については、次を参照してください。 [SharePoint プロジェクト システムの拡張機能でのデータの保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)です。  
  
## <a name="element-information"></a>要素情報
  
|||  
|-|-|  
|**名前空間**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel| 
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|いいえ|  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクト項目スキーマのリファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  
