---
title: 要素のファイル |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 15d771a53c0fb364aa363db8b6709257f41b9188
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2018
---
# <a name="files-element"></a>Files 要素
  フィーチャー要素ファイルなど、SharePoint プロジェクト項目と依存する以外の SharePoint プロジェクトの出力を配置するファイルを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## <a name="type"></a>型  
 **FileCollectionType**  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|省略可能な**ProjectItemFileType**要素。<br /><br /> フィーチャー要素ファイルが SharePoint に展開するときに、プロジェクト項目に含めるなどの SharePoint ファイルを表します。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|省略可能な**ProjectOutputFileType**要素。<br /><br /> SharePoint に配置されるときに、プロジェクト項目に含めるプロジェクトの出力を表します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクト項目を表します。 この要素の必須のルート要素の`.spdata`ファイル。|  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|**名前空間**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|いいえ|  
  
## <a name="see-also"></a>関連項目  
 [SharePoint プロジェクト項目スキーマのリファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  