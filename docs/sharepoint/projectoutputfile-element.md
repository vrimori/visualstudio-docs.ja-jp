---
title: ProjectOutputFile 要素 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 69af1992ba07fb75859a8f71bd0ee3eecadeaa0d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865334"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile 要素
  別のプロジェクトに含めるプロジェクト項目を SharePoint に配置されるときの出力を表します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## <a name="type"></a>型  
 **ProjectOutputFileType**  
  
## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**ProjectId**|必要な**xs:string**属性。<br /><br /> 追加する出力を持つ依存プロジェクトの GUID です。 これに対応して、 **ProjectGuid**依存プロジェクト ファイル内の要素。|  
|**ProjectPath**|必要な**xs:string**属性。<br /><br /> 含める出力を持つ依存プロジェクトのプロジェクト ファイル名を含む相対パス。 このパスは、SharePoint プロジェクト アイテムを含む SharePoint プロジェクトのルート フォルダーの相対パスです。|  
|**Target**|省略可能な**xs:string**属性。<br /><br /> 依存プロジェクトの出力が配置ルート フォルダーを基準とした、SharePoint サーバーに配置するパス。 配置ルート フォルダーがで指定された展開の種類によって決まりますが、**型**属性。<br /><br /> 詳細については、の説明を参照してください、**配置パス**と**Deployment Root** SharePoint のプロパティ内の項目をプロジェクト[SharePoint の開発ソリューション](../sharepoint/developing-sharepoint-solutions.md)します。|  
|**Type**|必要な**xs:string**属性。<br /><br /> 依存プロジェクトの出力に使用する展開の種類。 使用可能な値の詳細については、の説明を参照して、**展開の種類**で SharePoint プロジェクト アイテムのプロパティ[SharePoint の開発ソリューション](../sharepoint/developing-sharepoint-solutions.md)します。|  
  
### <a name="child-elements"></a>子要素
 なし。  
  
### <a name="parent-elements"></a>親要素
  
|要素|説明|  
|-------------|-----------------|  
|[ファイル](../sharepoint/files-element.md)|SharePoint に配置されるときに、SharePoint プロジェクト項目に含めるファイルを指定します。|  
  
## <a name="remarks"></a>Remarks  
 使用して、 **ProjectOutputFile**プロジェクトの出力を SharePoint プロジェクト アイテムの展開に含める要素。 別のプロジェクトまたはプロジェクト項目が含まれる同じプロジェクトを指定することができます。 詳細については、次を参照してください。[プロジェクト項目でパッケージ化と配置の情報を提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)します。  
  
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
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
