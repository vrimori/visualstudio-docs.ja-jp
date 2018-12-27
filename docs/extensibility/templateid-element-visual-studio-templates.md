---
title: TemplateID 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eda4b3134d8e7e589c60ee8b8860042b7e0f1ff5
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53560545"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID 要素 (Visual Studio テンプレート)
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