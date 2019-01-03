---
title: ProjectItemFile 要素 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f2c4446d8c0e3beff59a08cfbe6c0a6c9e5294d0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883917"
---
# <a name="projectitemfile-element"></a>ProjectItemFile 要素
  機能の要素ファイルが SharePoint に展開するときに、プロジェクト項目に含めるなど、SharePoint のファイルを表します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## <a name="type"></a>型  
 **ProjectItemFileType**  
  
## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**ソース**|必要な**xs:string**属性。<br /><br /> プロジェクト項目で展開するファイルの名前。|  
|**Target**|省略可能な**xs:string**属性。<br /><br /> ファイルが配置される、SharePoint のデプロイ ルート フォルダーの相対パス。 配置ルート フォルダーがで指定された展開の種類によって決まりますが、**型**属性。 場合、**ターゲット**属性が指定されていない、ファイルがで指定された名前のフォルダーに配置する、**ソース**属性。<br /><br /> 詳細については、の説明を参照してください、**配置パス**と**Deployment Root** SharePoint のプロパティ内の項目をプロジェクト[SharePoint の開発ソリューション](../sharepoint/developing-sharepoint-solutions.md)します。|  
|**Type**|必要な**xs:string**属性。<br /><br /> ファイルの展開の種類。 使用可能な値の詳細については、の説明を参照して、**展開の種類**で SharePoint プロジェクト アイテムのプロパティ[SharePoint の開発ソリューション](../sharepoint/developing-sharepoint-solutions.md)します。|  
  
### <a name="child-elements"></a>子要素
 なし。  
  
### <a name="parent-elements"></a>親要素
  
|要素|説明|  
|-------------|-----------------|  
|[ファイル](../sharepoint/files-element.md)|SharePoint に配置されるときに、SharePoint プロジェクト項目に含めるファイルを指定します。|  
  
## <a name="remarks"></a>Remarks  
 SharePoint ファイルで参照される通常**ProjectItemFile**要素がフィーチャー要素ファイルが含まれます (*Elements.xml*)、リスト定義のスキーマ ファイル (*Schema.xml*)、および Web パーツの Web パーツの定義ファイル (*.webpart*)。  
  
## <a name="element-information"></a>要素情報
  
|||  
|-|-|  
|**Namespace**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>SharePointProjectItemModel SharePointTools/2010/|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**ファイルの検証**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|いいえ|  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクト項目スキーマのリファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)  
