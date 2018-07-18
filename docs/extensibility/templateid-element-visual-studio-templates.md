---
title: TemplateID 要素 (Visual Studio テンプレート) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
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
ms.openlocfilehash: a7e431e603d0b2844431b5bffaedf7fa82bd7132
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138747"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID 要素 (Visual Studio テンプレート)
別の項目テンプレートのグループに分類される項目テンプレートの識別子を指定、 [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)要素。  
  
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
 A`string`では、項目テンプレートのグループに分類される項目テンプレートの識別子を表す、`TemplateGroupID`要素。  
  
## <a name="remarks"></a>コメント  
 `TemplateID` は、省略可能な要素です。  
  
 .Vstemplate ファイルを省略した場合、`TemplateID`要素、[名前](../extensibility/name-element-visual-studio-templates.md)要素は、テンプレートの識別子として使用します。  
  
 値、`TemplateID`要素は、プロジェクト システム登録と共に使用 (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\) に表示されるテンプレートをフィルター、**新しい項目の追加**ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)