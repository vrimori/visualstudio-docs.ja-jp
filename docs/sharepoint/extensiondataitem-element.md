---
title: "ExtensionDataItem 要素 |Microsoft ドキュメント"
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
helpviewer_keywords: ExtensionDataItem element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 65911101f7484b5e97d63df713c3e580c6964fe7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem 要素
  キー/値の形式で、SharePoint プロジェクト項目に関連付けられているカスタム データ項目を表します。 キーと値の両方には、文字列がある場合があります。  
  
## <a name="syntax"></a>構文  
  
```  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**Key**|必要な**xs:string**属性。<br /><br /> 格納およびデータ項目を取得するために使用するキー。|  
|**[値]**|必要な**xs:string**属性。<br /><br /> データ項目の値です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|SharePoint プロジェクト アイテムに関連付けられているカスタム データ項目のコレクションを表します。|  
  
## <a name="remarks"></a>コメント  
 ときにするデータを関連付けるカスタム SharePoint プロジェクト項目を使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>オブジェクト、Visual Studio を新しいデータを保存する**ExtensionDataItem**プロジェクト項目の .spdata ファイル内の要素。 詳細については、次を参照してください。 [SharePoint プロジェクト システムの拡張機能でのデータの保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)です。  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|**名前空間**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|×|  
  
## <a name="see-also"></a>参照  
 [SharePoint プロジェクト項目スキーマのリファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  