---
title: 要素のファイル |Microsoft Docs
ms.date: 02/02/2017
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
ms.openlocfilehash: e27e3192ec0d9a312c3cfc0a3521daf534c68e9a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922313"
---
# <a name="files-element"></a>Files 要素
  SharePoint プロジェクト項目の 機能の要素ファイルなど、および SharePoint 以外の依存プロジェクトの出力と共に配置するファイルを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## <a name="type"></a>型  
 **FileCollectionType**  
  
## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素
  
|要素|説明|  
|-------------|-----------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|省略可能な**ProjectItemFileType**要素。<br /><br /> 機能の要素ファイルが SharePoint に展開するときに、プロジェクト項目に含めるなど、SharePoint のファイルを表します。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|省略可能な**ProjectOutputFileType**要素。<br /><br /> SharePoint に展開するときに、プロジェクト項目に含めるプロジェクトの出力を表します。|  
  
### <a name="parent-elements"></a>親要素
  
|要素|説明|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクト項目を表します。 この要素の必須のルート要素の`.spdata`ファイル。|  
  
## <a name="element-information"></a>要素情報
  
|||  
|-|-|  
|**Namespace**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>SharePointProjectItemModel SharePointTools/2010/|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**ファイルの検証**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|いいえ|  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクト項目スキーマのリファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)  
