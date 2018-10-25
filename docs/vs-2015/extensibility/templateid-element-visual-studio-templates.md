---
title: TemplateID 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f287c7f1a7c8e9d134c99926f28d82399b837c0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188072"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

項目テンプレートでのグループに分類される項目テンプレートの識別子を指定します、 [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)要素。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<TemplateID >  
  
## <a name="syntax"></a>構文  
  
```  
<TemplateID> ... </TemplateID>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素です。<br /><br /> テンプレートをカテゴリに分類し、 **[新しいプロジェクト]** ダイアログ ボックス、または **[新しい項目の追加]** ダイアログ ボックスでどのように表示させるかを定義します。|  
  
## <a name="text-value"></a>テキスト値  
 A`string`は、項目テンプレートでのグループに分類される項目テンプレートの識別子を表す、`TemplateGroupID`要素。  
  
## <a name="remarks"></a>Remarks  
 `TemplateID` は、省略可能な要素です。  
  
 .Vstemplate ファイルを指定しない場合、`TemplateID`要素、[名前](../extensibility/name-element-visual-studio-templates.md)要素は、テンプレートの識別子として使用されます。  
  
 値、`TemplateID`要素は、プロジェクト システムの登録と使用 (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\) に表示されるフィルター テンプレートを**新しい項目の追加**ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)

