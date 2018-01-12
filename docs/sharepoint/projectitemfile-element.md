---
title: "ProjectItemFile 要素 |Microsoft ドキュメント"
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
helpviewer_keywords: ProjectItemFile element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7c222c25417f9a33f28871c94d8dd0d9353e1e76
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="projectitemfile-element"></a>ProjectItemFile 要素
  フィーチャー要素ファイルが SharePoint に展開するときに、プロジェクト項目に含めるなどの SharePoint ファイルを表します。  
  
## <a name="syntax"></a>構文  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## <a name="type"></a>型  
 **ProjectItemFileType**  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**ソース**|必要な**xs:string**属性。<br /><br /> プロジェクト項目と共に配置するファイルの名前。|  
|**Target**|省略可能な**xs:string**属性。<br /><br /> ファイルが配置される sharepoint には配置ルート フォルダーに対する相対パスです。 配置ルート フォルダーがで指定された展開の種類によって決まりますが、**型**属性。 場合、**ターゲット**属性が指定されていないファイルがで指定された名前のフォルダーに配置される場合、**ソース**属性。<br /><br /> 詳細については、の説明を参照してください、**配置パス**と**配置ルート**SharePoint のプロパティ内の項目をプロジェクト[SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|必要な**xs:string**属性。<br /><br /> ファイルの展開の種類。 使用可能な値の詳細については、の説明を参照して、**展開の種類**の SharePoint プロジェクト項目のプロパティ[SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[ファイル](../sharepoint/files-element.md)|SharePoint に配置されるときに、SharePoint プロジェクト項目に含めるファイルを指定します。|  
  
## <a name="remarks"></a>コメント  
 SharePoint のファイルで参照される通常**ProjectItemFile**フィーチャー要素ファイル (Elements.xml)、リスト定義 (Schema.xml) のスキーマ ファイルおよび Web パーツ定義ファイル (.webpart) の Web パーツの要素が含まれます。  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|**名前空間**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|×|  
  
## <a name="see-also"></a>参照  
 [SharePoint プロジェクト項目スキーマのリファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  