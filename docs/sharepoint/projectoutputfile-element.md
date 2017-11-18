---
title: "ProjectOutputFile 要素 |Microsoft ドキュメント"
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
helpviewer_keywords: ProjectOutputFile element
ms.assetid: 52a017bf-e19c-49e4-bb8f-cbe6958195c2
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a397648dd81ead8134777c8b36982fa6b65b687b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile 要素
  SharePoint に配置されるときに、プロジェクト項目に含める別のプロジェクトの出力を表します。  
  
## <a name="syntax"></a>構文  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## <a name="type"></a>型  
 **ProjectOutputFileType**  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**ProjectId**|必要な**xs:string**属性。<br /><br /> 追加する出力を持つ依存プロジェクトの GUID です。 これに対応して、 **ProjectGuid**依存プロジェクト ファイル内の要素。|  
|**ProjectPath**|必要な**xs:string**属性。<br /><br /> 相対パスをプロジェクト ファイル名を含めて、依存プロジェクトに含める出力を持ちます。 このパスを SharePoint プロジェクト項目を含む SharePoint プロジェクトのルート フォルダーに対する相対パスです。|  
|**Target**|省略可能な**xs:string**属性。<br /><br /> 依存プロジェクトの出力が配置ルート フォルダーを基準とした、SharePoint サーバーに配置するパス。 配置ルート フォルダーがで指定された展開の種類によって決まりますが、**型**属性。<br /><br /> 詳細については、の説明を参照してください、**配置パス**と**配置ルート**SharePoint のプロパティ内の項目をプロジェクト[SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|必要な**xs:string**属性。<br /><br /> 依存プロジェクトの出力に使用する展開の種類。 使用可能な値の詳細については、の説明を参照して、**展開の種類**の SharePoint プロジェクト項目のプロパティ[SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[ファイル](../sharepoint/files-element.md)|SharePoint に配置されるときに、SharePoint プロジェクト項目に含めるファイルを指定します。|  
  
## <a name="remarks"></a>コメント  
 使用して、 **ProjectOutputFile**にプロジェクトの出力を SharePoint プロジェクト項目の展開に含める要素。 別のプロジェクトまたはプロジェクト項目が含まれる同じプロジェクトを指定することができます。 詳細については、次を参照してください。[を提供するパッケージとプロジェクト項目での展開情報](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)です。  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|いいえ|  
  
## <a name="see-also"></a>関連項目  
 [SharePoint プロジェクト項目のスキーマ リファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [パッケージとプロジェクト アイテムの展開情報を提供します。](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
  