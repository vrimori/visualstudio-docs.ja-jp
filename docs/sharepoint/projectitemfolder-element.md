---
title: "ProjectItemFolder 要素 |Microsoft ドキュメント"
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
helpviewer_keywords: ProjectItemFolder element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: df3c5b91e5f95d6ec794bff08c2251c5bf5e5307
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder 要素
  マップされたフォルダーを表します。  
  
## <a name="syntax"></a>構文  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## <a name="type"></a>型  
 **ProjectItemFolderType**  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**Target**|必要な**xs:string**属性。<br /><br /> マップされたフォルダーが配置ルート フォルダーの相対パスに対応する SharePoint のインストール フォルダーのパス。 配置ルート フォルダーがで指定された展開の種類によって決まりますが、**型**属性。<br /><br /> 詳細については、の説明を参照してください、**配置パス**と**配置ルート**SharePoint のプロパティ内の項目をプロジェクト[SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|必要な**xs:string**属性。<br /><br /> マップされたフォルダーの展開の種類。 使用可能な値の詳細については、の説明を参照して、**展開の種類**の SharePoint プロジェクト項目のプロパティ[SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクト項目を表します。 .Spdata ファイルの必要なルート要素です。|  
  
## <a name="remarks"></a>コメント  
 マップされたフォルダーの詳細については、次を参照してください。[する方法: 追加し、マップされたフォルダーを削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)です。  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|**名前空間**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|×|  
  
## <a name="see-also"></a>参照  
 [SharePoint プロジェクト項目のスキーマ リファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [方法: マップされたフォルダーを追加および削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  