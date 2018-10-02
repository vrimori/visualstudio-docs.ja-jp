---
title: ProjectExtensions 要素 (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 156a35a953169c5b1ed8208c8d4f044f7b9fa36f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548579"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions 要素 (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ProjectExtensions 要素 (MSBuild)](https://docs.microsoft.com/visualstudio/msbuild/projectextensions-element-msbuild)します。  
  
  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] プロジェクト ファイルに、[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 以外の情報を含めることを可能にします。 `ProjectExtensions` 要素内のすべてのものは、[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] によって無視されます。  
  
 \<Project>  
 \<ProjectExtensions >  
  
## <a name="syntax"></a>構文  
  
```  
<ProjectExtensions>  
    Non-MSBuild information to include in file.  
</ProjectExtensions>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[プロジェクト](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] プロジェクト ファイルの必須のルート要素です。|  
  
## <a name="remarks"></a>Remarks  
 `ProjectExtensions` 要素は [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] プロジェクトで1 つだけ使用できます。  
  
## <a name="example"></a>例  
 次のコード例は、`ProjectExtensions` 要素に格納されている統合開発環境の情報を示します。  
  
```  
<ProjectExtensions>  
    <VSIDE>  
        <External>  
            <!--  
            Raw XML passed to the IDE by an external source  
            -->  
        </External>  
    </VSIDE>  
</ProjectExtensions>  
```  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト ファイル スキーマ リファレンス](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBuild](msbuild.md)


