---
title: "SafeControl 要素 |Microsoft ドキュメント"
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
helpviewer_keywords: SafeControl element
ms.assetid: e7c61749-fc73-412c-be30-4af5ff2a9fd2
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8d9651c320e574c8db9fcafcb6e98f13e45eac1d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="safecontrol-element"></a>SafeControl 要素
  ASPX コントロールまたは SharePoint サイト上の任意の ASPX ページにアクセスするすべてのユーザーのセキュリティで保護されたとして指定されている Web パーツを表します。  
  
## <a name="syntax"></a>構文  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**Assembly**|省略可能な**xs:string**属性。<br /><br /> ASPX コントロールまたは Web パーツが定義されているアセンブリの名前。 既定では、この属性を使用して、 **$SharePoint.Project.AssemblyFullName$**置き換え可能パラメーターをアセンブリ名。 詳細については、次を参照してください。[置き換え可能パラメーター](../sharepoint/replaceable-parameters.md)です。|  
|**IsSafe**|省略可能な**xs:boolean**属性。<br /><br /> ASPX コントロールまたは Web パーツが信頼されていないユーザーにアクセスするセキュリティで保護されたかどうかを指定します。|  
|**IsSafeAgainstScript**|省略可能な**xs:boolean**属性。<br /><br /> 信頼されていないユーザーを表示したり、ASPX コントロールまたは Web パーツのプロパティの編集にするかどうかを指定します。|  
|**名前**|省略可能な**xs:string**属性。<br /><br /> コレクション内には、この安全なコントロール エントリの名前。|  
|**Namespace**|省略可能な**xs:string**属性。<br /><br /> ASPX コントロールまたは Web パーツの名前空間。|  
|**型名**|省略可能な**xs:string**属性。<br /><br /> ASPX コントロールまたは Web パーツの型名。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|ASPX コントロールと、SharePoint サイト上の任意の ASPX ページにアクセスするすべてのユーザーのセキュリティで保護されたとして指定されている Web パーツのコレクションを表します。|  
  
## <a name="remarks"></a>コメント  
 安全なコントロールの詳細については、次を参照してください。[を提供するパッケージとプロジェクト項目での展開情報](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)です。  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**検証ファイル**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|いいえ|  
  
## <a name="see-also"></a>関連項目  
 [SharePoint プロジェクト項目のスキーマ リファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [プロジェクト項目でのパッケージ化と配置の情報の提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  